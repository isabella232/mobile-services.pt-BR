---
description: Após adicionar a biblioteca ao projeto, é possível executar todas as chamadas de método do Analytics em qualquer lugar no aplicativo (certifique-se de importar o ADBMobile.h para sua classe).
seo-description: Após adicionar a biblioteca ao projeto, é possível executar todas as chamadas de método do Analytics em qualquer lugar no aplicativo (certifique-se de importar o ADBMobile.h para sua classe).
seo-title: Analytics
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics {#analytics}

Após adicionar a biblioteca ao projeto, é possível executar todas as chamadas de método do Analytics em qualquer lugar no aplicativo (certifique-se de importar o ADBMobile.h para sua classe).

## Enable mobile application reports in Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

Antes de adicionar um código, peça para que um dos administradores do Analytics conclua as etapas a seguir para ativar o acompanhamento de Ciclo de vida do aplicativo móvel. Isso garante que o conjunto de relatórios esteja pronto para capturar métricas assim que você iniciar o desenvolvimento.


1. Open **[!UICONTROL Admin Tools]** &gt; **[!UICONTROL Report Suites]** and select your mobile report suite(s).
1. Click **[!UICONTROL Edit Settings]** &gt; **[!UICONTROL Mobile Management]** &gt; **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Clique em **[!UICONTROL Habilitar relatórios de aplicativo mais recentes]**.

   Opcionalmente, também é possível clicar em **[!UICONTROL Habilitar rastreamento de localização em dispositivos móveis]** e em **[!UICONTROL Habilitar Relatórios e atribuições herdados para ocorrências em segundo plano]**.

   ![](assets/enable-lifecycle.png)

Lifecycle metrics are now ready to be captured, and Mobile Application Reports] appear in the **[!UICONTROL Reports]** menu in the marketing reports interface.

## Coletar medições de ciclo de vida {#task_25D469C62DF84573AEB5E8E950B96205}

1. To collect lifecycle metrics in your app, call `collectLifecycleData()` in the `ApplicationUI` constructor.

   Por exemplo:

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   If `collectLifecycleData()` is called twice in the same session, then your application will report a crash on every call after the first. O SDK define um sinalizador quando o aplicativo é fechado que indica uma saída bem-sucedida. If this flag is not set, `collectLifecyleData()` reports a crash.

## Events, props, and eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


Se você tiver observado a Referência [de classe e método](/help/blackberry/methods.md)ADBMobile, provavelmente está se perguntando onde definir eventos, eVars, props, herdeiros e listas. Na versão 4, não é possível atribuir esses tipos de variáveis diretamente no aplicativo. Em vez disso, o SDK usa dados de contexto e regras de processamento de forma a mapear os dados do aplicativo para as variáveis do Analytics para criação de relatórios.

As regras de processamento oferecem diversas vantagens:

* Você pode alterar seu mapeamento de dados sem enviar uma atualização para a App Store.
* Como alternativa, use nomes significativos para os dados em vez de configurar variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados adicionais. Esses valores não aparecerão nos relatórios até que sejam mapeados usando regras de processamento.

Any values that you were assigning directly to variables should be added to the `data` HashMap instead.

## Regras de processamento {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

As regras de processamento são usadas para copiar os dados enviados nas variáveis de dados de contexto para evars, propriedades e outras variáveis para fins de criação e edição de relatórios.

[Treinamento sobre regras de processamento](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013

[Regras de processamento](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Receber autorização para usar as regras de processamento](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Recomendamos agrupar as variáveis de dados de contexto usando “namespaces”; isso o ajudará a manter uma ordem lógica. Por exemplo, se você quiser coletar informações sobre um produto, pode definir as seguintes variáveis:

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

As variáveis de dados de contexto são classificadas em ordem alfabética na interface das regras de processamento. Sendo assim, os namespaces permitem ver rapidamente as variáveis que estão no mesmo namespace.

Além disso, fomos informados de que alguns dos usuários têm nomeado as chaves de dados de contexto usando número do evar ou da propriedade:

```js
"eVar1":"jimbo"
```

Isso pode facilitar *um pouco* a execução do mapeamento único nas regras de processamento, mas você perderá a legibilidade durante a depuração e as futuras atualizações de código podem ser mais difíceis. Em vez disso, recomendamos o uso de nomes descritivos para chaves e valores:

```js
"username":"jimbo"
```

As variáveis de contexto que definem eventos de contagem podem ter a mesma chave e o mesmo valor:

```js
"logon":"logon"
```

As variáveis de contexto que definem eventos de incremento podem ter o evento como a chave e a quantidade a incrementar como o valor:

```js
"levels completed":"6"
```

>[!TIP]
>
>A Adobe reserva o namespace `a.`. Além dessa pequena restrição, as variáveis de dados de contexto só precisam ser únicas no logon da empresa para evitar conflitos.

## Ativar rastreamento offline {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

To store hits when the device is offline, you can optionally enable offline tracking in the `ADBMobileConfig.json` file.

Preste muita atenção às exigências do carimbo de data e hora descritas na referência do arquivo de configuração antes de habilitar o rastreamento offline.

## Analytics methods

Para obter uma lista dos métodos do Analytics disponíveis para o BlackBerry, consulte Métodos *do* Analytics em Referência [de métodos e classes do](/help/blackberry/methods.md)Adobe Mobile.