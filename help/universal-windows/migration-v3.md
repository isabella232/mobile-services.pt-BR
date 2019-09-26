---
description: Esta seção descreve como migrar da versão 3.x de um SDK móvel anterior do Windows para o SDK 4.x da plataforma Universal Windows Platform para Soluções da Experience Cloud.
seo-description: Esta seção descreve como migrar da versão 3.x de um SDK móvel anterior do Windows para o SDK 4.x da plataforma Universal Windows Platform para Soluções da Experience Cloud.
seo-title: Migrate to 4.x
solution: Marketing Cloud,Analytics
title: Migrar para 4.x
topic: Desenvolvedor e implementação
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrar para os SDKs 4.x{#migrate-to-x}

Esta seção descreve como migrar da versão 3.x do SDK móvel do Windows para o SDK 4.x da plataforma Universal Windows Platform para as soluções da Experience Cloud.

Com a mudança para a versão 4.x, toda a funcionalidade agora é acessível por meio de métodos estáticos. Não é mais necessário rastrear seus próprios objetos.

As seguintes seções o orientarão no processo de migração da versão 3.x para a 4.x.

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Você provavelmente notou um novo arquivo `ADBMobileConfig.json` incluído no seu download. Este arquivo contém configurações globais específicas do aplicativo e substitui a maioria das variáveis de configuração usadas em versões anteriores.

Este é um exemplo de um arquivo `ADBMobileConfig.json`:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
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

As tabelas a seguir listam as variáveis de configuração que você precisa mover para o arquivo de configuração. Mova o conjunto de valores para a variável na primeira coluna para a variável na segunda coluna e depois remova a variável configuração antiga do código.

### Migrar da versão 3.x

A tabela a seguir fornece uma lista de variáveis nos SDKs 3.x e o novo nome nos SDKs 4.x:

| Variável/método de configuração | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | "offlineEnabled" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| setOfflineHitLimit | Remover, não é mais usado. |
| linkTrackVars | Remover, não é mais usado. |
| linkTrackEvents | Remover, não é mais usado. |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Em vez de usar as chamadas com foco na Web `Track` e `TrackLink`, a versão 4 do SDK usa dois métodos que fazem mais sentido no mundo dos dispositivos móveis:

* `TrackState` Os estados são as visualizações que estão disponíveis no seu aplicativo, como “painel inicial”, “configurações do aplicativo”, “carrinho” e assim por diante. Esses estados são semelhantes às páginas em um site e as chamadas de `trackState` aumentam as exibições de página.

* `TrackAction` As ações são coisas que ocorrem no seu aplicativo e que deseja avaliar, como “logons”, “toques em banners”, “assinaturas de feed” e outras métricas. Estas chamadas não incrementam as exibições da página.

O parâmetro `contextData` para estes dois métodos contém os pares de nome e valor enviados como dados de contexto.

### Eventos, props, eVars

Se você observou os métodos [do](/help/universal-windows/c-configuration/methods.md)SDK, provavelmente está se perguntando onde definir eventos, eVars, props, herdeiros e listas. Na versão 4, não é possível atribuir esses tipos de variáveis diretamente no aplicativo. Em vez disso, o SDK usa dados de contexto e regras de processamento de forma a mapear os dados do aplicativo para as variáveis do Analytics para criação de relatórios.

As regras de processamento fornecem as seguintes vantagens:

* Você pode alterar seu mapeamento de dados sem enviar uma atualização para a App Store.
* Como alternativa, use nomes significativos para os dados em vez de configurar variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados adicionais. Esses valores não aparecerão nos relatórios até que sejam mapeados usando regras de processamento.

Para obter mais informações, consulte a seção Regras *de* processamento na visão geral [do](/help/universal-windows/analytics/analytics.md)Analytics.

Quaisquer valores atribuídos a variáveis devem ser, em vez disso, adicionados aos dados de contexto. This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

### AppSection/Server, GeoZip, transaction ID, Campaign, and other standard variables

Quaisquer outros dados configurados no objeto de medição, inclusive as variáveis listadas acima, devem ser adicionados aos dados de contexto em vez disso. Ou seja, os únicos dados enviados com uma `TrackState` ou `TrackAction` chamada são a carga no `data` parâmetro.

**Substituir chamadas de rastreamento**

Em todo o código, substitua os seguintes métodos por uma chamada a `trackState` ou `trackAction`:

**Migrar da versão 3.x:**

* TrackAppState (TrackState)
* TrackEvents (TrackAction)
* Track (TrackAction)
* TrackLinkURL (TrackAction)

## Serviço de ID personalizada {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

O rastreamento offline está ativado no `ADBMobileConfig.json` arquivo. Todas as outras configurações offline são feitas automaticamente.

Em todo o código, remova as chamadas aos métodos a seguir:

**Migrar da versão 3.x:**

* SetOnline
* SetOffline

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Como a variável não está disponível nas regras de processamento, você pode usar a seguinte sintaxe para definir `products`produtos:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

The value of `"&&products"` (in this example, the value is `";Cool Shoe`") should follow the products string syntax for the type of event that you are tracking.
