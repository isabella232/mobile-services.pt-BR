---
description: Esta seção descreve como migrar da versão 3.x de um SDK móvel anterior do Windows para o SDK 4.x da loja de aplicativos universal do Windows 8.1 para as soluções do Experience Cloud.
solution: Experience Cloud,Analytics
title: Migrar para os SDKs 4.x
topic-fix: Developer and implementation
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
exl-id: d6dc34f2-61b7-4026-a66a-19284e21e69c
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 25%

---

# Migrar para os SDKs 4.x {#migrate-to-the-x-sdks}

Esta seção descreve como migrar da versão 3.x de um SDK móvel anterior do Windows para o SDK 4.x da loja de aplicativos universal do Windows 8.1 para as soluções do Experience Cloud.

Com a mudança para a versão 4.x, toda a funcionalidade agora é acessível por meio de métodos estáticos, portanto, não é mais preciso rastrear seus próprios objetos.

As seções a seguir o orientam pela migração da versão 3.x para a 4.x.

## Remover propriedades não usadas {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Você provavelmente notou um novo arquivo `ADBMobileConfig.json` incluído no download. Esse arquivo contém configurações globais específicas do aplicativo e substitui a maioria das variáveis de configuração usadas em versões anteriores. Este é um exemplo de um arquivo `ADBMobileConfig.json`:

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

As tabelas a seguir listam as variáveis de configuração que você precisa mover para o arquivo de configuração. Mova o conjunto de valores para a variável na primeira coluna para a variável na segunda coluna e, em seguida, remova a variável de configuração antiga do seu código.

## Migrar do 3.x

| Variável/método de configuração | Variável no arquivo `ADBMobileConfig.json`. |
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

Em vez de usar as chamadas focadas na Web `Track` e `TrackLink`, o SDK versão 4 usa dois métodos que fazem um pouco mais de sentido no mundo móvel:

* `TrackState` Os estados são as exibições disponíveis no aplicativo, como &quot;painel inicial&quot;, &quot;configurações do aplicativo&quot;, &quot;carrinho&quot; e assim por diante. Esses estados são semelhantes às páginas em um site, e as chamadas de `trackState` aumentam as visualizações de página.

* `TrackAction` As ações são coisas que ocorrem no seu aplicativo e que deseja medir, como &quot;logons&quot;, &quot;toques em banners&quot;, &quot;assinaturas de feed&quot; e outras métricas. Essas chamadas não incrementam as exibições de página.

O parâmetro `contextData` para ambos os métodos contém pares de nome-valor enviados como dados de contexto.

## Eventos, Props, eVars

Se você tiver observado os [métodos do SDK](/help/windows-appstore/c-configuration/methods.md), provavelmente está se perguntando onde definir eventos, eVars, props, herdeiros e listas. Na versão 4, não é mais possível atribuir esses tipos de variáveis diretamente no aplicativo. Em vez disso, o SDK usa dados de contexto e regras de processamento para mapear os dados do aplicativo para as variáveis do Analytics para os relatórios.

As regras de processamento oferecem várias vantagens:

* Você pode alterar o mapeamento de dados sem enviar uma atualização para a loja de aplicativos.
* Você pode usar nomes significativos para dados em vez de definir variáveis específicas para um conjunto de relatórios.
* Há pouco impacto no envio de dados extras. Esses valores não aparecerão nos relatórios até que sejam mapeados usando as regras de processamento.

Para obter mais informações, consulte *Regras de processamento* em [Analytics](/help/windows-appstore/analytics/analytics.md).

Quaisquer valores atribuídos diretamente às variáveis devem ser adicionados aos dados de contexto. Isso significa que as chamadas para `SetProp`, `SetEvar` e as atribuições para dados de contexto persistentes devem ser removidas e os valores adicionados aos dados de contexto.

**AppSection/servidor, GeoZip, ID da transação, campanha e outras variáveis padrão**

Quaisquer outros dados que você estava configurando no objeto de medição, incluindo as variáveis listadas acima, devem ser adicionados aos dados de contexto.

Para simplificar, os únicos dados enviados com uma chamada `TrackState` ou `TrackAction` são a carga no parâmetro `data`.

### Substituir chamadas de rastreamento

Em todo o código, substitua os seguintes métodos com uma chamada para `trackState` ou `trackAction`:

### Migrar do 3.x

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## ID de visitante personalizada {#section_2CF930C13BA64F04959846E578B608F3}

Substitua a variável `visitorID` por uma chamada de `setUserIdentifier`.

## Rastreamento offline {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

O rastreamento offline é ativado no arquivo `ADBMobileConfig.json`. Todas as outras configurações offline são feitas automaticamente.

Em todo o código, remova chamadas para os seguintes métodos:

### Migrar do 3.x

* `SetOnline`
* `SetOffline`

## Variável products  {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Como a variável não está disponível nas regras de processamento, você pode usar a seguinte sintaxe para definir `products`produtos:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

Neste exemplo, o valor de `"&&products"` é `";Cool Shoe`&quot; e deve seguir a sintaxe da string de produtos para o tipo de evento que você está rastreando.
