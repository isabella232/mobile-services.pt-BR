---
description: 'null'
seo-description: 'null'
seo-title: Analytics
solution: Experience Cloud,Analytics
title: Analytics
topic-fix: Developer and implementation
uuid: fa0ef6c4-c04d-4695-9eb4-ada4e9920e6c
exl-id: 1a7b32b8-731d-4ae3-9feb-dafbb7495590
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 20%

---

# Analytics {#analytics}

Depois de adicionar a biblioteca ao seu projeto, você pode fazer qualquer uma das chamadas de método do Analytics em qualquer lugar no aplicativo.

>[!TIP]
>
>Certifique-se de importar `ADBMobile.h` para sua classe.

## Ativar relatórios de aplicativos móveis no Analytics {#section_F2F9234009184F20BA36B5CDE872B424}

Antes de adicionar o código, peça para que o administrador do Analytics conclua o seguinte procedimento para ativar o rastreamento do ciclo de vida do aplicativo móvel. Isso garante que seu conjunto de relatórios esteja pronto para capturar métricas assim que você começar o desenvolvimento.

1. Abra **[!UICONTROL Ferramentas administrativas]** > **[!UICONTROL Report Suites]** e selecione os seus conjuntos de relatórios móveis.
1. Clique em **[!UICONTROL Editar configurações]** > **[!UICONTROL Gerenciamento móvel]** > **[!UICONTROL Relatório de aplicativo móvel]**.

   ![](assets/mobile-settings.png)

1. Clique em **[!UICONTROL Ativar os Relatórios de Aplicativo mais recentes]**.

   Opcionalmente, também é possível clicar em **[!UICONTROL Ativar o rastreamento de localização em dispositivos móveis]** e **[!UICONTROL Ativar os relatórios e atribuições herdados para ocorrências em segundo plano]**.

   ![](assets/enable-lifecycle.png)

Agora, as medições de ciclo de vida estão prontas para serem capturadas, e os Relatórios de aplicativo móvel são exibidos no menu **[!UICONTROL Relatórios]** na interface dos relatórios de marketing.


### Novas versões

Periodicamente, novas versões dos relatórios de aplicativos móveis são lançadas. As novas versões não são aplicadas automaticamente ao seu conjunto de relatórios, você deve repetir essas etapas para executar a atualização. Cada vez que você adiciona uma nova funcionalidade do Experience Cloud ao seu aplicativo, recomendamos repetir essas etapas para garantir que você tenha a configuração mais recente.


## Métricas de ciclo de vida {#section_532702562A7A43809407C9A2CBA80E1E}

Para coletar medições de ciclo de vida no aplicativo, adicione chamadas para quando o aplicativo for ativado, como mostrado nos exemplos a seguir.


### WinJS no default.js


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

### C/CX em App.xaml.cpp

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

Se `CollectLifecycleData()` for chamado duas vezes na mesma sessão, o aplicativo reportará uma falha em cada chamada após a primeira. O SDK define um sinalizador quando o aplicativo é desligado, indicando uma saída bem-sucedida. Se esse sinalizador não estiver definido, `CollectLifecyleData()` relata uma falha.


## Eventos, propriedades e eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}


Se você tiver observado o [ADBMobile Class and Method Reference](/help/windows-appstore/c-configuration/methods.md), provavelmente está se perguntando onde definir eventos, eVars, props, herdeiros e listas. Na versão 4, não é mais possível atribuir esses tipos de variáveis diretamente no aplicativo. Em vez disso, o SDK usa dados de contexto e regras de processamento para mapear os dados do aplicativo para as variáveis do Analytics para os relatórios.

As regras de processamento oferecem várias vantagens:

* Você pode alterar o mapeamento de dados sem enviar uma atualização para a loja de aplicativos.
* Você pode usar nomes significativos para dados em vez de definir variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados extras. Esses valores não aparecerão nos relatórios até que sejam mapeados usando as regras de processamento.

Quaisquer valores atribuídos diretamente às variáveis devem ser adicionados aos dados de contexto.


## Regras de processamento {#section_66EE762EEA5E4728864166201617DEBF}

As regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para evars, props e outras variáveis de relatório.

[Treinamento em regras de processamento](https://tv.adobe.com/embed/1181/16506/) na Conferência de 2013

[Visão geral das regras de processamento](https://docs.adobe.com/content/help/pt-BR/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Receber autorização para usar as regras de processamento](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Recomendamos agrupar suas variáveis de dados de contexto usando &quot;namespaces&quot;, pois ajuda a manter uma ordem lógica. Por exemplo, se você quiser coletar informações sobre um produto, defina as seguintes variáveis:

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

As variáveis de dados de contexto são classificadas alfabeticamente na interface das regras de processamento, portanto, os namespaces permitem que você visualize rapidamente as variáveis que estão no mesmo namespace.

Além disso, ouvimos que alguns de você estão nomeando chaves de dados de contexto usando o número de evar ou prop:

```js
"eVar1":"jimbo"
```

Isso pode tornar *ligeiramente* mais fácil ao executar o mapeamento único nas regras de processamento, mas você perde a legibilidade durante a depuração e futuras atualizações de código podem ser mais difíceis. Em vez disso, recomendamos o uso de nomes descritivos para chaves e valores:

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

>[!NOTE]
>
>A Adobe reserva o namespace `a.`. Além dessa pequena restrição, as variáveis de dados de contexto só precisam ser únicas no logon da empresa para evitar colisões.

## Variável products {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Para definir *`products`* no SDK móvel, você deve usar uma sintaxe especial. Consulte [Variável de produtos](/help/windows-appstore/analytics/products/products.md).

## (Opcional) Ative o rastreamento offline {#section_955B2A03EB854742BDFC4A0A3C287009}

Para armazenar ocorrências quando o dispositivo estiver offline, é possível ativar o rastreamento offline na [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md). Antes de ativar o rastreamento offline, preste atenção aos requisitos do carimbo de data e hora descritos na referência do arquivo de configuração.

## Geolocalização e pontos de interesse {#section_BAD34A8DD013454DB355121316BD7FD4}

A localização geográfica permite medir dados de localização (latitude/longitude) e pontos de interesse predefinidos. Cada chamada `TrackLocation` envia:

* Latitude/longitude e POI (se dentro de um POI definido no arquivo de configuração `ADBMobileConfig.json`). Elas são passadas para variáveis de solução móvel para relatórios automáticos.
* Distância do centro e precisão transmitidas como dados de contexto. Capture usando uma regra de processamento.

Para rastrear uma localização:

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

Se o seguinte POI estiver definido no arquivo de configuração `ADBMobileConfig.json`:

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

Quando a localização do dispositivo é determinada como estando dentro de um raio de 7000 metros do ponto definido, uma variável `a.loc.poi` dos dados de contexto com o valor &quot;São Francisco&quot; é enviada com a ocorrência `TrackLocation`. Uma variável de contexto `a.loc.dist` é enviada com a distância em metros a partir das coordenadas definidas.

## Valor vitalício {#section_D2C6971545BA4D639FBE07F13EF08895}

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

As ações cronometradas permitem medir o tempo no aplicativo e o tempo total entre o início e o fim de uma ação. O SDK calcula a quantidade de tempo na sessão e o tempo total (entre sessões) necessário para a ação ser concluída. Isso pode ser usado para definir segmentos que serão comparados no momento da compra, no nível de passagem, no fluxo de finalização da compra e assim por diante.

* Número total de segundos no aplicativo entre o início e o término - sessões cruzadas
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
