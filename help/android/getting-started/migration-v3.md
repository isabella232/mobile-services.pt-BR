---
description: Essas informações ajudam a migrar das versões 3.x ou 2.x da biblioteca do Android para a versão 4.x.
keywords: android;library;mobile;sdk
seo-description: Essas informações ajudam a migrar das versões 3.x ou 2.x da biblioteca do Android para a versão 4.x.
seo-title: Migrar para a biblioteca do Android 4.x
solution: Marketing Cloud,Analytics
title: Migrar para a biblioteca do Android 4.x
topic: Desenvolvedor e implementação
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrating to the Android 4.x library {#migrating-to-the-android-x-library}

Essas informações ajudam a migrar das versões 3.x ou 2.x da biblioteca do Android para a versão 4.x.

>[!IMPORTANT]
>
>The SDK uses `SharedPreferences` to store data that is needed to calculate unique users, lifecycle metrics, and other data related to core SDK functionality.  Se modificar ou remover os valores no `SharedPreferences` esperados pelo SDK, pode resultar um comportamento inesperado na forma de inconsistência de dados.

Na biblioteca da versão 4.x, os métodos públicos são consolidados em um cabeçalho. Além disso, todas as funcionalidades agora são acessíveis pelos métodos de nível de classe, sendo assim, não é preciso rastrear os ponteiros, instâncias ou singletons.

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

Na versão 4, não é mais possível designar variáveis como events, eVars, props, heirs e lists no aplicativo. Em vez disso, o SDK usa dados de contexto e regras de processamento de forma a mapear os dados do aplicativo para as variáveis do Analytics para relatório.

As regras de processamento fornecem as seguintes vantagens:

* Você pode alterar seu mapeamento de dados sem enviar uma atualização para a App Store.
* Como alternativa, use nomes significativos para os dados em vez de configurar variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados adicionais.

   Esses valores não aparecerão nos relatórios até serem mapeados usando regras de processamento.

>[!TIP]
>
>Values that you assigned directly to variables should be added to the `data` HashMap.

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

## Moving the configuration file and migrating to version 4 {#section_0B844235E0B04DD4B36976A73DB28FB5}

As tabelas a seguir listam as variáveis de configuração que você precisa mover para o arquivo de configuração.

### Mover o arquivo de configuração

1. Mova o valor definido para a variável na primeira coluna para a variável na segunda coluna.
1. Remova a variável de configuração antiga do seu código.

### Migrar da versão 3.x

Para migrar da versão 3.x para a 4, mova o valor da variável/método de configuração para a `ADBMobileConfig.json` variável.

| Variável ou método de configuração | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| setOfflineTrackingEnabled | "offlineEnabled" |
| setOfflineHitLimit | "batchLimit" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | Remover, não é mais usado. |
| linkTrackEvents | Remover, não é mais usado. |

### Migrar da versão 2.x

Para migrar da versão 2.x para a 4, mova o valor da primeira coluna para a variável na segunda coluna.

| Variável de configuração | Variable in the `ADBMobileConfig.json` file |
| --- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server", remova o `"https://"` prefixo. O prefixo do protocolo é adicionado automaticamente com base na configuração "ssl". |
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
| useBestPractices  todas as chamadas para medição de rotatividade (getChurnInstance) | Remover, substituído por Medições de ciclo de vida. |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Em vez de usar as chamadas focadas na Web `track` e `trackLink`, o SDK versão 4 usa os seguintes métodos:

* `trackState`, que são as exibições disponíveis no aplicativo, como `home dashboard`, `app settings`, `cart`etc.

   Esses estados são semelhantes às páginas em um site e as chamadas de `trackState` aumentam as exibições de página.

* `trackAction` ações, como `logons`, `banner taps`, `feed subscriptions`etc., que ocorrem no aplicativo e que você deseja avaliar.

The `contextData` parameter for both of these methods is a `HashMap<String, Object>`, which contains the name-value pairs that are sent as context data.

## Eventos, props e eVars

Na versão 4, não é mais possível designar variáveis como eventos, eVars, propriedades, herdeiros e listas diretamente no aplicativo. O SDK agora usa dados de contexto e regras de processamento para mapear os dados do seu aplicativo para variáveis do Analytics para gerar relatórios.

As regras de processamento fornecem as seguintes vantagens:

* Você pode alterar seu mapeamento de dados sem enviar uma atualização para a App Store.
* Como alternativa, use nomes significativos para os dados em vez de configurar variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados adicionais.

   Esses valores não aparecerão nos relatórios até que sejam mapeados usando as regras de processamento. Para obter mais informações, consulte Regras [de processamento e Dados](/help/android/getting-started/proc-rules.md)de contexto.

Values that you were assigning directly to variables should be added to the `data` HashMap. This means that calls to `setProp`, `setEvar`, and assignments to persistent context data should be removed and the values be added to the `data` parameter.

## AppSection/server, GeoZip, transaction ID, Campaign, and other standard variables

Data that you were setting on the measurement object, including the variables listed above, should be added to the `data` HashMap. Os únicos dados enviados com uma chamada `trackState` ou `trackAction` são a carga no parâmetro `data`.

### Replace tracking calls

Substitua os seguintes métodos com uma chamada para `trackState` ou `trackAction`:

* **Migrar da versão 3.x**

   * `trackAppState (trackState)`
   * `trackEvents (trackAction)`
   * `track (trackAction)`
   * `trackLinkURL (trackAction)`

* **Migrar da versão 2.x**

   * `track (trackState)`
   * `trackLink (trackAction)`

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file, and all other offline configuration is done automatically.

Remova chamadas dos seguintes métodos:

**Versão 3.x**

* `setOnline`
* `setOffline`

**Versão 2.x**

* `forceOffline`
* `forceOnline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

For more information about the products variable, see [Products variable](/help/android/analytics-main/products/products.md).

