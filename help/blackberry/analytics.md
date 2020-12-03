---
description: Depois de adicionar a biblioteca ao seu projeto, você pode efetuar qualquer uma das chamadas de método do Analytics em qualquer lugar no seu aplicativo (certifique-se de importar ADBMobile.h para sua classe).
seo-description: Depois de adicionar a biblioteca ao seu projeto, você pode efetuar qualquer uma das chamadas de método do Analytics em qualquer lugar no seu aplicativo (certifique-se de importar ADBMobile.h para sua classe).
seo-title: Analytics
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 14%

---


# Analytics {#analytics}

Depois de adicionar a biblioteca ao seu projeto, você pode efetuar qualquer uma das chamadas de método do Analytics em qualquer lugar no seu aplicativo (certifique-se de importar ADBMobile.h para sua classe).

## Ativar relatórios de aplicativos móveis no Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

Antes de adicionar o código, peça para que o administrador do Analytics conclua o seguinte para ativar o rastreamento do ciclo de vida do aplicativo móvel. Isso garante que seu conjunto de relatórios esteja pronto para capturar métricas à medida que você iniciar o desenvolvimento.


1. Abra Ferramentas **** administrativas > **[!UICONTROL Report Suites]** e selecione seus report suites móveis.
1. Clique em **[!UICONTROL Editar configurações]** > Gerenciamento **** móvel > Relatórios **[!UICONTROL do aplicativo]** móvel.

   ![](assets/mobile-settings.png)

1. Clique em **[!UICONTROL Ativar os relatórios]** mais recentes do aplicativo.

   Opcionalmente, você também pode clicar em **[!UICONTROL Ativar rastreamento]** de localização móvel e **[!UICONTROL Ativar Relatórios e atribuição herdados para ocorrências]** em segundo plano.

   ![](assets/enable-lifecycle.png)

As medições de ciclo de vida estão prontas para serem capturadas e os Relatórios de aplicativo móvel são exibidos no menu **[!UICONTROL Relatórios]** na interface dos relatórios de marketing.

## Coletar medições de ciclo de vida {#task_25D469C62DF84573AEB5E8E950B96205}

1. Para coletar medições de ciclo de vida em seu aplicativo, chame `collectLifecycleData()` o `ApplicationUI` construtor.

   Por exemplo:

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   Se `collectLifecycleData()` for chamado duas vezes na mesma sessão, o aplicativo reportará uma falha em cada chamada após a primeira. O SDK define um sinalizador quando o aplicativo é desligado que indica uma saída bem-sucedida. Se esse sinalizador não estiver definido, `collectLifecyleData()` reportará uma falha.

## Eventos, propriedades e eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


Se você tiver observado a Referência [de método e classe](/help/blackberry/methods.md)ADBMobile, provavelmente está se perguntando onde definir eventos, eVars, props, herdeiros e listas. Na versão 4, não é mais possível atribuir esses tipos de variáveis diretamente no aplicativo. Em vez disso, o SDK usa dados de contexto e regras de processamento para mapear os dados do aplicativo para as variáveis do Analytics para os relatórios.

As regras de processamento oferecem várias vantagens:

* Você pode alterar o mapeamento de dados sem enviar uma atualização para a loja de aplicativos.
* Você pode usar nomes significativos para dados em vez de definir variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados extras. Esses valores não aparecerão nos relatórios até que sejam mapeados usando as regras de processamento.

Any values that you were assigning directly to variables should be added to the `data` HashMap instead.

## Regras de processamento {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

As regras de processamento são usadas para copiar os dados enviados nas variáveis de dados de contexto para evars, props e outras variáveis do relatórios.

[Treinamento em regras de processamento](https://tv.adobe.com/embed/1181/16506/) na Conferência de 2013

[Regras de processamento](https://docs.adobe.com/content/help/pt-BR/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Receber autorização para usar as regras de processamento](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Recomendamos agrupar as variáveis de dados de contexto usando &quot;namespace&quot;, pois isso ajuda a manter a ordem lógica. Por exemplo, se você deseja coletar informações sobre um produto, pode definir as seguintes variáveis:

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

As variáveis de dados de contexto são classificadas em ordem alfabética na interface das regras de processamento, de modo que o namespace permite que você veja rapidamente as variáveis que estão na mesma namespace.

Além disso, ouvimos que alguns de vocês estão nomeando chaves de dados de contexto usando o número de evar ou prop:

```js
"eVar1":"jimbo"
```

This might make it *slightly* easier when you perform the one time mapping in processing rules, but you lose readability during debugging and future code updates can be more difficult. Em vez disso, recomendamos o uso de nomes descritivos para chaves e valores:

```js
"username":"jimbo"
```

As variáveis de contexto que definem eventos de contador podem ter a mesma chave e valor:

```js
"logon":"logon"
```

As variáveis de dados de contexto que definem eventos de incremento podem ter o evento como a chave e o valor a incrementar como o valor:

```js
"levels completed":"6"
```

>[!TIP]
>
>A Adobe reserva o namespace `a.`. Além dessa pequena restrição, as variáveis de dados de contexto só precisam ser exclusivas na sua empresa de logon para evitar colisões.

## Ativar rastreamento offline {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

Para armazenar ocorrências quando o dispositivo estiver offline, é possível ativar o rastreamento offline no `ADBMobileConfig.json` arquivo.

Preste muita atenção aos requisitos de carimbo de data e hora descritos na referência do arquivo de configuração antes de ativar o rastreamento offline.

## Métodos do Analytics

Para obter uma lista dos métodos do Analytics disponíveis para o BlackBerry, consulte Métodos *do* Analytics em Referência [de métodos e classes móveis do](/help/blackberry/methods.md)Adobe.