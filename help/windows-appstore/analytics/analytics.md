---
description: 'null'
seo-description: 'null'
seo-title: Analytics
solution: Marketing Cloud, Analytics
title: Analytics
topic: Desenvolvedor e implementação
uuid: fa 0 ef 6 c 4-c 04 d -4695-9 eb 4-ada 4 e 9920 e 6 c
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Analytics {#analytics}

Depois de adicionar a biblioteca ao seu projeto, você pode fazer quaisquer chamadas de método do Analytics em qualquer lugar no aplicativo.

>[!TIP]
>
>Certifique-se de importar `ADBMobile.h` para a sua classe.

## Enable mobile application reports in Analytics {#section_F2F9234009184F20BA36B5CDE872B424}

Antes de adicionar um código, peça para que um dos administradores do Analytics conclua as etapas a seguir para ativar o acompanhamento de Ciclo de vida do aplicativo móvel. Isso garante que o conjunto de relatórios esteja pronto para capturar métricas assim que você iniciar o desenvolvimento.

1. Open **[!UICONTROL Admin Tools]** &gt; **[!UICONTROL Report Suites]** and select your mobile report suite(s).
1. Click **[!UICONTROL Edit Settings]** &gt; **[!UICONTROL Mobile Management]** &gt; **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Clique em **[!UICONTROL Habilitar relatórios de aplicativo mais recentes]**.

   Opcionalmente, também é possível clicar em **[!UICONTROL Habilitar rastreamento de localização em dispositivos móveis]** e em **[!UICONTROL Habilitar Relatórios e atribuições herdados para ocorrências em segundo plano]**.

   ![](assets/enable-lifecycle.png)

As métricas de ciclo de vida estão prontas para serem capturadas, e os Relatórios de aplicativo móvel são exibidos no menu **Relatórios**, na interface dos relatórios de marketing.


### Novas versões

Periodicamente, novas versões dos relatórios de aplicativo para dispositivos móveis são lançadas. As novas versões não são aplicadas a seu conjunto de relatórios automaticamente, é necessário repetir essas etapas para realizar a atualização. Cada vez que você adicionar uma nova funcionalidade da Experience Cloud ao aplicativo, recomendamos que repita essas etapas para garantir a configuração mais recente.


## Lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

Para coletar métricas de ciclo de vida no aplicativo, adicione chamadas para quando o aplicativo estiver ativado, como mostrado nos exemplos a seguir.


### Winjs em default. js


```js
app.onactivated = function (args) { 
  if (args.detail.kind === activation.ActivationKind.launch) { 
   ... 
   // launched and resumed stuff  
   ADBMobile.Config.collectLifecycleData(); 
  } 
}; 
app.oncheckpoint = function (args) { 
  ADBMobile.Config.pauseCollectingLifecycleData(); 
}
```

### C # em App. xaml. cs

```js
public App() 
{ 
    this.InitializeComponent(); 
    this.Resuming *= OnResuming; 
    this.Suspending *= OnSuspending; 
} 
protected override void OnLaunched(LaunchActivatedEventArgs e) 
{ 
    ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnResuming(object sender, object e) 
{ 
    ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnSuspending(object sender, SuspendingEventArgs e) 
{ 
    ... 
    ADBMobile.Config.PauseCollectingLifecycleData(); 
    ... 
}
```

### C/CX em App. xaml. cpp

```js
App::App() 
{ 
 InitializeComponent(); 
 Resuming *= ref new EventHandler<Object ^>(this, &App::OnResuming); 
 Suspending *= ref new SuspendingEventHandler(this, &App::OnSuspending); 
} 
void App::OnResuming(Object ^sender, Object ^args) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
} 
void App::OnSuspending(Object^ sender, SuspendingEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::PauseCollectingLifecycleData(); 
 ... 
} 
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
}
```

If `CollectLifecycleData()` is called twice in the same session, then your application will report a crash on every call after the first. O SDK define um sinalizador quando o aplicativo é fechado que indica uma saída bem-sucedida. If this flag is not set, `CollectLifecyleData()` reports a crash.


## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}


Se você olhou a Referência do [adbmobile Class e de métodos](/help/windows-appstore/c-configuration/methods.md), talvez você esteja se perguntando onde definir eventos, evars, props, herdeiros e listas. Na versão 4, não é possível atribuir esses tipos de variáveis diretamente no aplicativo. Em vez disso, o SDK usa dados de contexto e regras de processamento de forma a mapear os dados do aplicativo para as variáveis do Analytics para criação de relatórios.

As regras de processamento oferecem diversas vantagens:

* Você pode alterar seu mapeamento de dados sem enviar uma atualização para a App Store.
* Como alternativa, use nomes significativos para os dados em vez de configurar variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados adicionais. Esses valores não aparecerão nos relatórios até que sejam mapeados usando regras de processamento.

Quaisquer valores atribuídos a variáveis devem ser, em vez disso, adicionados aos dados de contexto.


## Regras de processamento {#section_66EE762EEA5E4728864166201617DEBF}

As regras de processamento são usadas para copiar os dados enviados nas variáveis de dados de contexto para evars, propriedades e outras variáveis para fins de criação e edição de relatórios.

[Treinamento sobre regras de processamento](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013

[Visão geral das regras de processamento](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Receber autorização para usar regras de processamento](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

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

Configure variáveis de contexto que definem eventos de contagem com o valor “1”:

```js
"logon":"1"
```

As variáveis de dados de contexto que definem eventos do incrementador podem ter o valor a incrementar:

```js
"levels completed":"6"
```

>[!NOTE]
>
>A Adobe reserva o namespace `a.`. Além dessa pequena restrição, as variáveis de dados de contexto só precisam ser únicas no logon da empresa para evitar conflitos.

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Para definir *`products`* no SDK móvel, é necessário usar uma sintaxe especial. Consulte [Variável de produtos](/help/windows-appstore/analytics/products/products.md).

## (Optional) Enable offline tracking {#section_955B2A03EB854742BDFC4A0A3C287009}

To store hits when the device is offline, you can enable offline tracking in the [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md). Antes de habilitar o rastreamento offline, preste atenção para os requisitos de carimbo de data e hora descritos na referência do arquivo de configuração.

## Geo-location and points of interest {#section_BAD34A8DD013454DB355121316BD7FD4}

A localização geográfica permite medir dados de localização (latitude/longitude) e pontos de interesse predefinidos. Each `TrackLocation` call sends:

* Latitude/longitude e pontos de interesse (se em um ponto de interesse definido no arquivo de configuração `ADBMobileConfig.json`). Eles são passados para as variáveis de soluções móveis para relatórios automáticos.
* A distância do centro e a precisão transmitida como dados de contexto. Capture usando uma regra de processamento.

Para rastrear uma localização:

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

Se o seguinte ponto de interesse estiver definido no arquivo de configuração `ADBMobileConfig.json`:

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

Quando a localização do dispositivo é determinada como estando dentro de um raio de 7.000 metros do ponto definido, uma variável de dados de contexto `a.loc.poi` com o valor “San Francisco” é enviada com a ocorrência `TrackLocation`. Uma variável de contexto `a.loc.dist` também é enviada com a distância em metros das coordenadas definidas.

## Lifetime value {#section_D2C6971545BA4D639FBE07F13EF08895}

O valor de tempo de vida permite medir e atingir um valor para cada usuário. Cada vez que um valor é enviado com `TrackLifetimeValueIncrease`, o valor é adicionado ao valor existente. O valor de tempo de vida é armazenado no dispositivo e pode ser recuperado a qualquer momento ao chamar `GetLifetimeValue`. Isso pode ser usado para armazenar compras de tempo de vida, exibições de anúncios, conclusões de vídeos, compartilhamentos nas redes sociais, carregamentos de fotos e assim por diante.

```js
// Lifetime Value Example 
var ADB = ADBMobile; 
var purchasePrice = 39.95; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ItemPurchaseEvent"] = "ItemPurchaseEvent"; 
cdata["PurchaseItem"] = "Item453"; 
cdata["PurchasePrice"] = purchasePrice; 
ADB.Analytics.trackLifetimeValueIncrease(purchasePrice, cdata);
```

## Timed actions {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

As ações cronometradas permitem medir o tempo no aplicativo e o tempo total entre o início e o fim de uma ação. O SDK calcula o tempo da sessão e o total de tempo (entre sessões) necessário para completar a ação. É possível usar isso para definir segmentos para comparar na hora de comprar, passar de nível, do fluxo de checkout e outros.

* Número total de segundos no aplicativo entre as sessões de início e de término - sessões cruzadas
* Número total de segundos entre o início e o término (hora do relógio)

```js
// Timed Action Start Example 
var ADB = ADBMobile; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ExperienceName"] = experience; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
```

```js
// Timed Action Update Example 
var ADB = ADBMobile; 
var cdataUpdate = new Windows.Foundation.Collections.PropertySet(); 
cdataUpdate["ImageLiked"] = imageName; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
```

```js
// Timed Action End Example 
var ADB = ADBMobile; 
ADB.Analytics.trackTimedActionEnd("TimeUntilPurchase");
```
