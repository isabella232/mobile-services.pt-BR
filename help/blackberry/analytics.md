---
description: Após adicionar a biblioteca ao seu projeto, é possível realizar qualquer uma das chamadas de método do Analytics em qualquer lugar no aplicativo (certifique-se de importar o ADBMobile.h para sua classe).
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
exl-id: 4cd27e1a-e806-4dbb-84f5-63902ca2003f
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 13%

---

# Analytics {#analytics}

Após adicionar a biblioteca ao seu projeto, é possível realizar qualquer uma das chamadas de método do Analytics em qualquer lugar no aplicativo (certifique-se de importar o ADBMobile.h para sua classe).

## Ativar relatórios de aplicativos móveis no Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

Antes de adicionar o código, peça para que o administrador do Analytics conclua o seguinte procedimento para ativar o rastreamento do ciclo de vida do aplicativo móvel. Essas ações garantem que o conjunto de relatórios esteja pronto para capturar métricas assim que você começar o desenvolvimento.

1. Abra **[!UICONTROL Ferramentas administrativas]** > **[!UICONTROL Report Suites]** e selecione os seus conjuntos de relatórios móveis.
1. Clique em **[!UICONTROL Editar configurações]** > **[!UICONTROL Gerenciamento móvel]** > **[!UICONTROL Relatório de aplicativo móvel]**.

   ![Configurações móveis](assets/mobile-settings.png)

1. Clique em **[!UICONTROL Ativar os Relatórios de Aplicativo mais recentes]**.

   Opcionalmente, também é possível clicar em **[!UICONTROL Ativar o rastreamento de localização em dispositivos móveis]** e **[!UICONTROL Ativar os relatórios e atribuições herdados para ocorrências em segundo plano]**.

   ![Ativar ciclo de vida](assets/enable-lifecycle.png)

Agora, as medições de ciclo de vida estão prontas para serem capturadas, e os Relatórios de aplicativo móvel são exibidos no menu **[!UICONTROL Relatórios]** na interface dos relatórios de marketing.

## Coletar medições de ciclo de vida {#task_25D469C62DF84573AEB5E8E950B96205}

1. Para coletar medições de ciclo de vida no aplicativo, chame `collectLifecycleData()` no construtor `ApplicationUI`.

   Por exemplo:

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   Se `collectLifecycleData()` for chamado duas vezes na mesma sessão, o aplicativo reportará uma falha em cada chamada após a primeira. O SDK define um sinalizador quando o aplicativo é desligado, indicando uma saída bem-sucedida. Se esse sinalizador não estiver definido, `collectLifecyleData()` relata uma falha.

## Eventos, propriedades e eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}

Se você tiver observado o [ADBMobile Class and Method Reference](/help/blackberry/methods.md), provavelmente está se perguntando onde definir eventos, eVars, props, herdeiros e listas. Na versão 4, não é mais possível atribuir esses tipos de variáveis diretamente no aplicativo. Em vez disso, o SDK usa dados de contexto e regras de processamento para mapear os dados do aplicativo para as variáveis do Analytics para os relatórios.

As regras de processamento oferecem várias vantagens:

* Você pode alterar o mapeamento de dados sem enviar uma atualização para a loja de aplicativos.
* Você pode usar nomes significativos para dados em vez de definir variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados extras. Esses valores não aparecerão nos relatórios até que sejam mapeados usando as regras de processamento.

Quaisquer valores atribuídos diretamente às variáveis devem ser adicionados ao HashMap `data`.

## Regras de processamento {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

As regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para eVars, props e outras variáveis de relatório.

[Treinamento em regras de processamento](https://tv.adobe.com/embed/1181/16506/) na Conferência de 2013

[Regras de processamento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Receber autorização para usar as regras de processamento](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Recomendamos agrupar suas variáveis de dados de contexto usando &quot;namespaces&quot;, pois ajuda a manter uma ordem lógica. Por exemplo, se você quiser coletar informações sobre um produto, defina as seguintes variáveis:

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

As variáveis de dados de contexto são classificadas alfabeticamente na interface das regras de processamento, portanto, os namespaces permitem que você visualize rapidamente as variáveis que estão no mesmo namespace.

Além disso, ouvimos que alguns de você estão nomeando chaves de dados de contexto usando o eVar ou número de propriedade:

```js
"eVar1":"jimbo"
```

Isso pode tornar *ligeiramente* mais fácil ao executar o mapeamento único nas regras de processamento, mas você perde a legibilidade durante a depuração e futuras atualizações de código podem ser mais difíceis. Em vez disso, recomendamos o uso de nomes descritivos para chaves e valores:

```js
"username":"jimbo"
```

As variáveis de contexto que definem eventos de contador podem ter a mesma chave e valor:

```js
"logon":"logon"
```

As variáveis de dados de contexto que definem eventos de incremento podem ter o evento como a chave e a quantidade a ser incrementada como o valor:

```js
"levels completed":"6"
```

>[!TIP]
>
>A Adobe reserva o namespace `a.`. Além dessa pequena restrição, as variáveis de dados de contexto só precisam ser únicas no logon da empresa para evitar colisões.

## Habilitar rastreamento offline {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

Para armazenar ocorrências quando o dispositivo estiver offline, é possível ativar o rastreamento offline no arquivo `ADBMobileConfig.json`.

Preste muita atenção aos requisitos do carimbo de data e hora descritos na referência do arquivo de configuração antes de ativar o rastreamento offline.

## Métodos do Analytics

Para obter uma lista dos métodos do Analytics disponíveis para o BlackBerry, consulte *Métodos do Analytics* em [Referência de método e classe móvel do Adobe](/help/blackberry/methods.md).
