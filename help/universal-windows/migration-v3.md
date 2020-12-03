---
description: Esta seção descreve como migrar da versão 3.x de um SDK móvel anterior do Windows para o SDK 4.x da plataforma Universal Windows Platform para Soluções Experience Cloud.
seo-description: Esta seção descreve como migrar da versão 3.x de um SDK móvel anterior do Windows para o SDK 4.x da plataforma Universal Windows Platform para Soluções Experience Cloud.
seo-title: Migrar para 4.x
solution: Experience Cloud,Analytics
title: Migrar para 4.x
topic: Developer and implementation
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 26%

---


# Migrar para os SDKs 4.x{#migrate-to-x}

Esta seção descreve como migrar da versão 3.x do SDK móvel do Windows para o SDK 4.x da plataforma Universal Windows Platform para Soluções Experience Cloud.

Com a mudança para a versão 4.x, toda a funcionalidade agora é acessível por meio de métodos estáticos. Não é mais necessário rastrear seus próprios objetos.

As seções a seguir o orientam pela migração da versão 3.x para a versão 4.x.

## Remover propriedades não usadas {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Você provavelmente notou um novo `ADBMobileConfig.json` arquivo incluído no download. Este arquivo contém configurações globais específicas do aplicativo e substitui a maioria das variáveis de configuração usadas em versões anteriores.

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

As tabelas a seguir listam as variáveis de configuração que você precisa mover para o arquivo de configuração. Mova o valor definido para a variável na primeira coluna para a variável na segunda coluna e remova a variável de configuração antiga do seu código.

### Migração do 3.x

A tabela a seguir fornece uma lista de variáveis nos SDKs 3.x e o novo nome nos SDKs 4.x:

| Variável/método de configuração | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| setOfflineHitLimit | Remover, não é mais usado. |
| linkTrackVars | Remover, não é mais usado. |
| linkTrackEvents | Remover, não é mais usado. |

## Atualizar chamadas e variáveis de rastreamento {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Em vez de usar o SDK da versão 4 `Track` e `TrackLink` chamadas voltadas para a Web, ele usa dois métodos que fazem um pouco mais de sentido no mundo móvel:

* `TrackState` Os estados são as visualizações que estão disponíveis no aplicativo, como &quot;painel inicial&quot;, &quot;configurações do aplicativo&quot;, &quot;carrinho&quot; e assim por diante. Esses estados são semelhantes às páginas em um site, e as chamadas de `trackState` aumentam as visualizações de página.

* `TrackAction` As ações são coisas que ocorrem no aplicativo e que você deseja avaliar, como &quot;logons&quot;, &quot;toques em banners&quot;, &quot;subscrições de feed&quot; e outras métricas. Essas chamadas não incrementam visualizações de página.

The `contextData` parameter for both of these methods contains name-value pairs that are sent as context data.

### Eventos, propriedades, eVars

Se você observou os métodos [do](/help/universal-windows/c-configuration/methods.md)SDK, provavelmente está se perguntando onde definir eventos, eVars, props, herdeiros e listas. Na versão 4, não é mais possível atribuir esses tipos de variáveis diretamente no aplicativo. Em vez disso, o SDK usa dados de contexto e regras de processamento para mapear os dados do aplicativo para as variáveis do Analytics para os relatórios.

As regras de processamento oferecem as seguintes vantagens:

* Você pode alterar o mapeamento de dados sem enviar uma atualização para a loja de aplicativos.
* Você pode usar nomes significativos para dados em vez de definir variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados extras. Esses valores não aparecerão nos relatórios até que sejam mapeados usando as regras de processamento.

Para obter mais informações, consulte a seção Regras *de* processamento na visão geral [do](/help/universal-windows/analytics/analytics.md)Analytics.

Quaisquer valores atribuídos diretamente às variáveis devem ser adicionados aos dados de contexto. This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

### AppSection/servidor, GeoZip, ID da transação, campanha e outras variáveis padrão

Quaisquer outros dados que você estivesse configurando no objeto de medição, incluindo as variáveis listadas acima, devem ser adicionados aos dados de contexto. Ou seja, os únicos dados enviados com uma `TrackState` ou `TrackAction` chamada são a carga no `data` parâmetro.

**Substituir chamadas de rastreamento**

Throughout your code, replace the following methods with a call to `trackState` or `trackAction`:

**Migração do 3.x:**

* TrackAppState (TrackState)
* TrackEvents (TrackAction)
* Track (TrackAction)
* TrackLinkURL (TrackAction)

## Serviço de ID personalizada {#section_2CF930C13BA64F04959846E578B608F3}

Substitua a variável `visitorID` por uma chamada de `setUserIdentifier`.

## Rastreamento offline {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file. All other offline configuration is done automatically.

Em todo o código, remova chamadas para os seguintes métodos:

**Migração do 3.x:**

* SetOnline
* SetOffline

## Variável products {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Como a variável não está disponível nas regras de processamento, você pode usar a seguinte sintaxe para definir `products`produtos:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

O valor de `"&&products"` (neste exemplo, o valor é `";Cool Shoe`&quot;) deve seguir a sintaxe da string products para o tipo de evento que você está rastreando.
