---
description: Estas informações ajudam a migrar da versão 3.x ou 2.x da biblioteca do iOS para a versão 4.x.
seo-description: Estas informações ajudam a migrar da versão 3.x ou 2.x da biblioteca do iOS para a versão 4.x.
seo-title: Migrating to the 4.x iOS library
solution: Marketing Cloud,Analytics
title: Migração para a biblioteca 4.x do iOS
topic: Desenvolvedor e implementação
uuid: 5668972b-f355-4e03-9df0-8c82ddf6809b
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrating to the 4.x iOS library{#migrating-to-the-x-ios-library}

Estas informações ajudam a migrar da versão 3.x ou 2.x da biblioteca do iOS para a versão 4.x.

>[!IMPORTANT]
>
>The SDK uses `NSUserDefaults` to store data that is needed to calculate unique users, lifecycle metrics, and other data related to core SDK functionality.  Se modificar ou remover os valores no `NSUserDefaults` esperados pelo SDK, pode resultar um comportamento inesperado na forma de inconsistência de dados.

In the version 4.x of the iOS SDK library, the public methods are consolidated into one header. Além disso, a funcionalidade agora está acessível por meio de métodos de nível de classe, portanto, não é necessário rastrear ponteiros, instâncias ou singletons.

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

Na versão 4, você não pode mais atribuir variáveis como eventos, eVars, props, herdeiros e listas diretamente no seu aplicativo. Em vez disso, o SDK usa dados de contexto e regras de processamento para mapear os dados do seu aplicativo para variáveis do Analytics para gerar relatórios.

As regras de processamento fornecem as seguintes vantagens:

* Você pode alterar seu mapeamento de dados sem enviar uma atualização para a App Store.
* Como alternativa, use nomes significativos para os dados em vez de configurar variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados adicionais.

   Esses valores não aparecerão nos relatórios até serem mapeados usando regras de processamento.

>[!TIP]
>
>Values that you were assigning directly to variables should now be added to the `data` NSDictionary.

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

O novo arquivo `ADBMobileConfig.json` contém configurações globais específicas do aplicativo e substitui a maioria das variáveis de configuração usadas em versões anteriores. Este é um exemplo de um arquivo `ADBMobileConfig.json`:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 5, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 5 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```


### Mover o arquivo de configuração

Para mover o arquivo de configuração:

1. Mova o valor definido para a variável na primeira coluna para a variável na segunda coluna.
1. Remova a variável de configuração antiga do seu código.

### Migration information

As tabelas a seguir listam as variáveis de configuração que você precisa mover para o arquivo de configuração.

#### Migrar da versão 3.x

Mova o valor da primeira coluna para a variável na segunda coluna.

| Variável de configuração | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| offlineTrackingEnabled | "offlineEnabled" |
| offlineHitLimit | "batchLimit" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | Remover, não é mais usado. |
| linkTrackEvents | Remover, não é mais usado. |


#### Migrar da versão 2.x

Mova o valor da primeira coluna para a variável na segunda coluna.

| Variável de configuração | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server", remove the  prefix. `"https://"` O prefixo do protocolo é adicionado automaticamente com base na configuração "ssl". |
| trackingServerSecure | Remover. Para conexões seguras, defina "server" e ative "ssl". |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | Remover, não é mais usado. |
| linkTrackEvents | Remover, não é mais usado. |
| timestamp | Remover, não pode mais ser configurado. |
| dc | Remover, não é mais usado. |
| userAgent | Remover, não pode mais ser configurado. |
| dynamicVariablePrefix | Remover, não é mais usado. |
| visitorNamespace | Remover, não é mais usado. |
| usePlugins | Remover, não é mais usado. |
| useBestPractices  todas as chamadas para medição de rotatividade (getChurnInstance ) | Remove, replaced by lifecycle metrics. Para obter mais informações, consulte [Medições de ciclo de vida](//help/ios/metrics.md). |


## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Em vez de usar as chamadas focadas na Web `track` e `trackLink`, o SDK versão 4 usa os seguintes métodos:

* `trackState:data:` estados são as exibições disponíveis no aplicativo, como `home dashboard`, `app settings`, `cart`etc.

   Esses estados são semelhantes às páginas em um site e as chamadas de `trackState` aumentam as exibições de página.

* `trackAction:data:` ações, como `logons`, `banner taps`e `feed subscriptions`outras métricas que ocorrem no aplicativo e que você deseja avaliar.

O parâmetro `data` para ambos os métodos é um `NSDictionary` que contém os pares de nomes/valores enviados como dados de contexto.

### Eventos, props, eVars

Na versão 4, não é mais possível designar variáveis como eventos, eVars, propriedades, herdeiros e listas diretamente no aplicativo. O SDK agora usa dados de contexto e regras de processamento para mapear os dados do seu aplicativo para variáveis do Analytics para gerar relatórios.

As regras de processamento fornecem as seguintes vantagens:

* Você pode alterar seu mapeamento de dados sem enviar uma atualização para a App Store.
* Como alternativa, use nomes significativos para os dados em vez de configurar variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados adicionais.

   Esses valores não aparecerão nos relatórios até serem mapeados usando regras de processamento. Para obter mais informações, consulte [Regras de processamento e dados de contexto](/help/ios/getting-started/proc-rules.md).

Os valores atribuídos diretamente às variáveis devem ser adicionados ao `data``NSDictionary` . This means that calls to `setProp`, `setEvar`, and assignments to persistent context data should all be removed and the values be added to the `data` parameter.

### AppSection/Server, GeoZip, ID de transação, Campanha e outras variáveis padrão

Os dados que você estava configurando no objeto de medição, incluindo as variáveis listadas acima, devem ser adicionados ao `data``NSDictionary`   em vez disso. Os únicos dados enviados com uma chamada `trackState` ou `trackAction` são a carga no parâmetro `data`.

### Substituir chamadas de rastreamento

No seu código, substitua os seguintes métodos com uma chamada para `trackState` ou `trackAction`:

#### Migrar da versão 3.x

* `trackAppState (trackState)`
* `trackEvents (trackAction)`
* `track (trackAction)`
* `trackWithContextData (trackAction)`
* `trackLinkURL (trackAction)`

#### Migrar da versão 2.x

* `track (trackState)`
* `trackLink (trackAction)`

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier:`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file, and all other offline configuration is done automatically.

No seu código, remova chamadas para os seguintes métodos:

### Versão 3.x

* `setOnline`
* `setOffline`

### Versão 2.x

* `forceOffline`
* `forceOnline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Como a variável não está disponível nas regras de processamento, você pode usar a seguinte sintaxe para definir `products`produtos:

```objective-c
//create a processing rule to set the corresponding product event. 
// for example, set prodView event when context data a.action = "product view" 
[ADBMobile trackAction:@"LikeButtonClicked"  
                  data:@{@"&&products" : @";Cool Shoe"}];
```

![](assets/prod-view.png)