---
description: Essas informações ajudam a migrar das versões 3.x ou 2.x da biblioteca do Android para a versão 4.x.
keywords: android;biblioteca;móvel;sdk
solution: Experience Cloud Services,Analytics
title: Migrar para a biblioteca do Android 4.x
topic-fix: Developer and implementation
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
exl-id: 8061c1ab-aaaf-4d4c-9bd5-b2f80b6b06a3
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 99%

---

# Migração para a biblioteca do Android 4.x {#migrating-to-the-android-x-library}

Essas informações ajudam a migrar das versões 3.x ou 2.x da biblioteca do Android para a versão 4.x.

>[!IMPORTANT]
>
>O SDK usa o `SharedPreferences` para armazenar dados necessários para calcular usuários únicos, métricas de ciclo de vida e outros dados relacionados à funcionalidade principal do SDK.  Se modificar ou remover os valores no `SharedPreferences` esperados pelo SDK, pode resultar um comportamento inesperado na forma de inconsistência de dados.

Na versão 4.x da biblioteca, os métodos públicos são consolidados em um único cabeçalho. Além disso, a funcionalidade agora pode ser acessada por meio de métodos de nível de classe; portanto, não é necessário acompanhar cursores, instâncias ou singletons.

## Eventos, propriedades e eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

Na versão 4, não é mais possível atribuir variáveis como eventos, eVars, props, herdeiros e listas no aplicativo. Em vez disso, o SDK usa dados de contexto e regras de processamento para mapear os dados do aplicativo para as variáveis do Analytics para os relatórios.

As regras de processamento oferecem as seguintes vantagens:

* Você pode alterar o mapeamento de dados sem enviar uma atualização para a loja de aplicativos.
* Você pode usar nomes significativos para dados em vez de definir variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados extras.

   Esses valores não aparecerão nos relatórios até que sejam mapeados usando as regras de processamento.

>[!TIP]
>
>Os valores atribuídos diretamente às variáveis devem ser adicionados ao `data` HashMap.

## Remover propriedades não usadas {#section_145222EAA20F4CC2977DD883FDDBBFC5}

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

## Mover o arquivo de configuração e migrando para a versão 4 {#section_0B844235E0B04DD4B36976A73DB28FB5}

As tabelas a seguir listam as variáveis de configuração que você precisa mover para o arquivo de configuração.

### Mover o arquivo de configuração

1. Mova o valor definido para a variável na primeira coluna para a variável na segunda coluna.
1. Remova a variável de configuração antiga do seu código.

### Migrar da versão 3.x

Para migrar da versão 3.x para a 4, mova o valor da variável/método de configuração para a variável `ADBMobileConfig.json`.

| Variável ou método de configuração | Variável no arquivo `ADBMobileConfig.json` |
|--- |--- |
| setOfflineTrackingEnabled | &quot;offlineEnabled&quot; |
| setOfflineHitLimit | “batchLimit” |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | Remover, não é mais usado. |
| linkTrackEvents | Remover, não é mais usado. |

### Migrar da versão 2.x

Para migrar da versão 2.x para a 4, mova o valor da primeira coluna para a variável na segunda coluna.

| Variável de configuração | Variável no arquivo `ADBMobileConfig.json` |
| --- |--- |
| trackOffline | &quot;offlineEnabled&quot; |
| offlineLimit | “batchLimit” |
| account | &quot;rsids&quot; |
| trackingServer | &quot;server&quot;, remover o prefixo `"https://"`. O prefixo do protocolo é adicionado automaticamente com base na configuração &quot;ssl&quot;. |
| trackingServerSecure | Remover. Para conexões seguras, defina &quot;server&quot; e ative &quot;ssl&quot;. |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | Remover, não é mais usado. |
| linkTrackEvents | Remover, não é mais usado. |
| carimbo de data e hora | Remover, não é mais configurável. |
| dc | Remover, não é mais usado. |
| userAgent | Remover, não é mais configurável. |
| dynamicVariablePrefix | Remover, não é mais usado. |
| visitorNamespace | Remover, não é mais usado. |
| usePlugins | Remover, não é mais usado. |
| useBestPractices  todas as chamadas para medição de churn (getChurnInstance) | Remover, substituído por Métricas de ciclo de vida. |

## Atualizar chamadas e variáveis de rastreamento {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Em vez de usar as chamadas focadas na Web `track` e `trackLink`, o SDK versão 4 usa os seguintes métodos:

* `trackState`, que são as exibições disponíveis no aplicativo, como `home dashboard`, `app settings`, `cart` e assim por diante.

   Esses estados são semelhantes às páginas em um site, e as chamadas de `trackState` aumentam as visualizações de página.

* ações `trackAction`, como `logons`, `banner taps`, `feed subscriptions`, entre outras, que ocorrem no aplicativo e que você deseja medir.

O parâmetro `contextData` para os dois métodos é um `HashMap<String, Object>`, que contém os pares de nome-valor enviados como dados de contexto.

## Eventos, propriedades e eVars

Na versão 4, não é mais possível atribuir variáveis como eventos, eVars, props, herdeiros e listas diretamente no aplicativo. O SDK agora usa dados de contexto e regras de processamento para mapear os dados do aplicativo para as variáveis do Analytics para os relatórios.

As regras de processamento oferecem as seguintes vantagens:

* Você pode alterar o mapeamento de dados sem enviar uma atualização para a loja de aplicativos.
* Você pode usar nomes significativos para dados em vez de definir variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados extras.

   Esses valores não aparecerão nos relatórios até que sejam mapeados usando as regras de processamento. Para obter mais informações, consulte [Regras de processamento e Dados de contexto](/help/android/getting-started/proc-rules.md).

Os valores designados às variáveis devem ser adicionados ao HashMap `data`. Isso significa que as chamadas para `setProp`, `setEvar` e atribuições para dados de contexto persistentes devem ser removidas e os valores devem ser adicionados ao parâmetro `data`.

## AppSection/servidor, GeoZip, ID da transação, campanha e outras variáveis padrão

Os dados que você estava configurando no objeto de medição, incluindo as variáveis listadas acima, devem ser adicionados ao HashMap `data`. Os únicos dados enviados com uma chamada `trackState` ou `trackAction` são a carga no parâmetro `data`.

### Substituir chamadas de rastreamento

Substitua os seguintes métodos com uma chamada para `trackState` ou `trackAction`:

* **Migrar da versão 3.x**

   * `trackAppState (trackState)`
   * `trackEvents (trackAction)`
   * `track (trackAction)`
   * `trackLinkURL (trackAction)`

* **Migrar da versão 2.x**

   * `track (trackState)`
   * `trackLink (trackAction)`

## ID de visitante personalizada {#section_2CF930C13BA64F04959846E578B608F3}

Substitua a variável `visitorID` por uma chamada de `setUserIdentifier`.

## Rastreamento offline {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

O rastreamento offline está habilitado no arquivo `ADBMobileConfig.json` e todas as outras configurações offline são feitas automaticamente.

Remova as chamadas para os seguintes métodos:

**Versão 3.x**

* `setOnline`
* `setOffline`

**Versão 2.x**

* `forceOffline`
* `forceOnline`

## Variável products  {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Para obter mais informações sobre a variável products, consulte [Variável products](/help/android/analytics-main/products/products.md).
