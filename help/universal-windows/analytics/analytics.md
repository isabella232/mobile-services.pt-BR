---
description: 'null'
seo-description: 'null'
seo-title: Analytics
solution: Experience Cloud,Analytics
title: Analytics
topic: Developer and implementation
uuid: c2cef3d3-77a7-4a8e-bbe4-3db10a77996a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 11%

---


# Analytics {#analytics}

Depois de adicionar a biblioteca ao seu projeto, você pode fazer qualquer uma das chamadas de método do Analytics em qualquer lugar no aplicativo.

>[!TIP]
>
>Certifique-se de importar `ADBMobile.h` para sua classe.

## Ativar relatórios de aplicativos móveis no Analytics {#section_F2F9234009184F20BA36B5CDE872B424}

Antes de adicionar o código, peça para que o administrador do Analytics conclua o seguinte para ativar o rastreamento do ciclo de vida do aplicativo móvel. Isso garante que seu conjunto de relatórios esteja pronto para capturar métricas à medida que você iniciar o desenvolvimento.

1. Abra Ferramentas **** administrativas > **[!UICONTROL Report Suites]** e selecione seus report suites móveis.

1. Clique em **[!UICONTROL Editar configurações]** > Gerenciamento **** móvel > Relatórios **[!UICONTROL do aplicativo]** móvel.

   ![](assets/mobile-settings.png)

1. Clique em **[!UICONTROL Ativar os relatórios]** mais recentes do aplicativo.

   Opcionalmente, você também pode clicar em **[!UICONTROL Ativar rastreamento]** de localização móvel ou em **[!UICONTROL Ativar Relatórios e atribuição herdados para ocorrências]** em segundo plano.

   ![](assets/enable-lifecycle.png)

As medições de ciclo de vida estão prontas para serem capturadas e os Relatórios de aplicativo móvel são exibidos no menu **[!UICONTROL Relatórios]** na interface dos relatórios de marketing.

### Novas versões

Periodicamente, novas versões do relatórios de aplicativo móvel são lançadas. As novas versões não são aplicadas automaticamente ao seu conjunto de relatórios, você deve repetir essas etapas para executar a atualização. Sempre que você adicionar uma nova funcionalidade de Experience Cloud ao seu aplicativo, recomendamos que repita essas etapas para garantir que você tenha a configuração mais recente.

## Métricas de ciclo de vida {#section_532702562A7A43809407C9A2CBA80E1E}

Para coletar medições de ciclo de vida em seu aplicativo, adicione chamadas para quando o aplicativo for ativado, como mostrado nos exemplos a seguir.

### WinJS em default.js

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

### C# em App.xaml.cs

```js
public App() 
{ 
    this.InitializeComponent(); 
    this.Resuming += OnResuming; 
    this.Suspending += OnSuspending; 
} 
protected override void OnLaunched(LaunchActivatedEventArgs e) 
{   ... 
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

### C++/CX em App.xaml.cpp

```js
App::App() 
{ 
 InitializeComponent(); 
 Resuming += ref new EventHandler<Object ^>(this, &App::OnResuming); 
 Suspending += ref new SuspendingEventHandler(this, &App::OnSuspending); 
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

Se `CollectLifecycleData()` for chamado duas vezes na mesma sessão, seu aplicativo reportará uma falha em cada chamada após a primeira. O SDK define um sinalizador quando o aplicativo é desligado que indica uma saída bem-sucedida. Se esse sinalizador não estiver definido, `CollectLifecyleData()` reportará uma falha.

## Eventos, propriedades e eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

Se você observou os métodos [do](/help/universal-windows/c-configuration/methods.md)SDK, provavelmente está se perguntando onde definir eventos, eVars, props, herdeiros e listas. Na versão 4, não é mais possível atribuir esses tipos de variáveis diretamente no aplicativo. Em vez disso, o SDK usa dados de contexto e regras de processamento para mapear os dados do aplicativo para as variáveis do Analytics para o relatórios.

As regras de processamento oferecem várias vantagens:

* Você pode alterar o mapeamento de dados sem enviar uma atualização para a App Store.
* Você pode usar nomes significativos para dados em vez de definir variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados extras. Esses valores não aparecerão nos relatórios até que sejam mapeados usando as regras de processamento.

Quaisquer valores atribuídos diretamente às variáveis devem ser adicionados aos dados de contexto.

## Regras de processamento {#section_66EE762EEA5E4728864166201617DEBF}

As regras de processamento são usadas para copiar os dados enviados nas variáveis de dados de contexto para evars, props e outras variáveis do relatórios.

[Treinamento](https://tv.adobe.com/embed/1181/16506/) das regras de processamento no Summit 2013

[Ajuda das regras de processamento](https://docs.adobe.com/content/help/pt-BR/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Receber autorização para usar as regras de processamento](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Recomendamos agrupar as variáveis de dados de contexto usando &quot;namespace&quot;, pois isso ajuda a manter a ordem lógica. Por exemplo, se você deseja coletar informações sobre um produto, pode definir as seguintes variáveis:

```javascript
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

As variáveis de dados de contexto são classificadas em ordem alfabética na interface das regras de processamento, de modo que o namespace permite que você veja rapidamente as variáveis que estão na mesma namespace.

Além disso, ouvimos que alguns de vocês estão nomeando chaves de dados de contexto usando o número de evar ou prop:

```js
"eVar1":"jimbo"
```

Isso pode tornar *um pouco* mais fácil ao executar o mapeamento único nas regras de processamento, mas você perde a legibilidade durante a depuração e as futuras atualizações de código podem ser mais difíceis. Em vez disso, recomendamos o uso de nomes descritivos para chaves e valores:

```js
"username":"jimbo"
```

Defina variáveis de contexto que definem eventos de contador com um valor de &quot;1&quot;:

```js
"logon":"1"
```

As variáveis de dados de contexto que definem eventos de incremento podem ter o valor a incrementar:

```js
"levels completed":"6"
```

>[!TIP]
>
>A Adobe reserva o namespace `a.`. Além dessa restrição, as variáveis de dados de contexto precisam ser exclusivas na empresa de logon para evitar colisões.

## Variável products {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Para configurar *`products`* no SDK móvel, é necessário usar uma sintaxe especial. Para obter mais informações, consulte Variável [](/help/universal-windows/analytics/products.md)de produtos.

## (Opcional) Habilitar rastreamento offline {#section_955B2A03EB854742BDFC4A0A3C287009}

Para armazenar ocorrências quando o dispositivo estiver offline, é possível ativar o rastreamento offline no arquivo de métodos [do](/help/universal-windows/c-configuration/methods.md) SDK. Preste atenção aos requisitos de carimbo de data e hora descritos na referência do arquivo de configuração antes de ativar o rastreamento offline.

## Geolocalização e pontos de interesse {#section_BAD34A8DD013454DB355121316BD7FD4}

A localização geográfica permite medir os dados de localização (latitude/longitude) e os pontos de interesse predefinidos. Cada `TrackLocation` chamada envia:

* Latitude/longitude e POI (se estiver dentro de um POI definido no arquivo de `ADBMobileConfig.json` configuração).

   Elas são transmitidas para variáveis de solução móvel para relatórios automático.

* Distância do centro e precisão transmitida como dados de contexto.

   Capture usando uma regra de processamento.

Para rastrear um local:

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

Se o seguinte POI estiver definido no arquivo de `ADBMobileConfig.json` configuração:

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

Quando o local do dispositivo é determinado como estando dentro de um raio de 7.000 metros do ponto definido, uma variável de dados de `a.loc.poi` contexto com o valor `San Francisco` é enviada com a `TrackLocation` ocorrência. An `a.loc.dist` context variable is sent with the distance in meters from the defined coordinates.

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

## Ações cronometradas {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

As ações cronometradas permitem medir o tempo no aplicativo e o tempo total entre o start e o fim de uma ação. O SDK calcula a quantidade de tempo na sessão e o tempo total (entre sessões) necessário para a ação ser concluída. Isso pode ser usado para definir segmentos a serem comparados na hora da compra, no nível de passagem, no fluxo de checkout e assim por diante.

* Número total de segundos no aplicativo entre o start e as sessões de término
* Número total de segundos entre o start e o término (hora do relógio)

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
