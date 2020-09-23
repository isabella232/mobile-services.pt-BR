---
description: A geolocalização ajuda a avaliar os dados de localização usando latitude, longitude e pontos de interesse predefinidos em aplicativos do Android.
seo-description: A geolocalização ajuda a avaliar os dados de localização usando latitude, longitude e pontos de interesse predefinidos em aplicativos do Android.
seo-title: Geolocalização e pontos de interesse
solution: Experience Cloud,Analytics
title: Geolocalização e pontos de interesse
topic: Developer and implementation
uuid: b8209370-cbc4-40f9-97d8-017e2d74a377
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 83%

---


# Geolocalização e pontos de interesse {#geo-location-and-points-of-interest}

A geolocalização ajuda a avaliar os dados de localização usando latitude, longitude e pontos de interesse predefinidos em aplicativos do Android.

Cada chamada `trackLocation` envia as seguintes informações:

* Latitude, longitude e localização de um ponto de interesse (POI) definido na interface do usuário do Adobe Mobile Services.

   Essas informações são passadas para variáveis de solução móvel para relatórios automático.

* Distância do centro e precisão transmitida como dados de contexto.

   Essas variáveis não são capturadas automaticamente. Você deve mapear essas variáveis de dados de contexto usando as instruções em *Envio de dados adicionais* na seção abaixo.

## Atualização de POI dinâmico {#section_3747B310DD5147E2AAE915E762997712}

A partir da versão 4.2, os POIs são definidos na interface do usuário do Adobe Mobile e sincronizados dinamicamente com o arquivo de configuração do aplicativo. Esta sincronização requer uma configuração `analytics.poi` na [Configuração JSON do ADBMobile](/help/android/configuration/json-config/json-config.md):

```js
“analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”,
```

Se não estiver configurado, é necessário baixar uma versão atualizada do arquivo `ADBMobile.json` e adicioná-la ao aplicativo. Para obter mais informações, consulte [Download do SDK e Ferramentas de teste](/help/android/getting-started/requirements.md).

## Rastreamento de geolocalização e POIs {#section_B1616E400A7548F9A672F97FEC75AE27}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto IntelliJ IDEA ou Eclipse* na [Implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Importe a biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Chame `trackLocation` para rastrear a localização atual:

   ```java
   Location currentLocation = new Location("my location here"); 
   Analytics.trackLocation(currentLocation, null);
   ```

   >[!TIP]
   >
   >Você pode chamar `trackLocation` a qualquer momento.

   É possível usar as estratégias de localização para determinar a localização passada para a chamada `trackLocation`. Para obter mais informações, consulte [Estratégias de localização do Android](https://developer.android.com/guide/topics/location/strategies.html).

Além disso, se a localização estiver determinada a estar em um raio de POI definido, uma variável `a.loc.poi` dos dados de contexto é enviada com a ocorrência `trackLocation`, além de ser relatada como um POI nos relatórios do **[!UICONTROL Detalhamento de localização]**. Uma variável de contexto `a.loc.dist` também é enviada com a distância em metros a partir das coordenadas definidas.

## Envio de dados adicionais {#section_3EBE813E54A24F6FB669B2478B5661F9}

Além dos dados de localização, você pode enviar dados de contexto adicionais com cada chamada de localização de rastreamento:

```java
HashMap<String, Object> locationContextData = new HashMap<String, Object>(); 
locationContextData.put("myapp.location.LocationSource", "GPS"); 
 
Location currentLocation = new Location("my location here"); 
Analytics.trackLocation(currentLocation, locationContextData);
```

Os valores de dados de contexto devem ser mapeados para variáveis personalizadas na interface do usuário do Adobe Mobile Services:

![](assets/map-location-context-data.png)

## Dados do contexto de localização {#section_FFB71E6653F9410A89CC6ACC0C9164A9}

A latitude e a longitude são enviadas usando três parâmetros de dados de contexto diferentes, com cada parâmetro representando um nível diferente de precisão, para um total de seis parâmetros de dados de contexto.

Por exemplo, as coordenadas lat = 40.93231, long = -111.93152 representam um local com precisão de 1 m. Esse local é dividido de acordo com o nível de precisão nas seguintes variáveis:

`a.loc.lat.a`= 040.9

`a.loc.lat.b` = 32

`a.loc.lat.c` = 31

`a.loc.lon.a` = -111,9

`a.loc.lon.b` = 31

`a.loc.lon.c` = 52

Alguns níveis de precisão podem aparecer como `00`, dependendo da precisão da localização atual. Por exemplo, se a localização tiver uma precisão de 100 m, `a.loc.lat.c` e `a.loc.lon.c` serão preenchidos com `00`.

Lembre-se das seguintes informações:

* Uma solicitação `trackLocation` envia o equivalente a uma chamada `trackAction`.

* Os POIs não são passados como chamadas `trackAction` e `trackState` típicas, então você deve usar uma chamada `trackLocation` para rastrear os POIs.

* A `trackLocation` deve ser chamada sempre que necessário para rastrear a localização e os POIs.

   Recomendamos fazer uma chamada com a `trackLocation` quando o aplicativo for iniciado e conforme for necessário, dependendo das solicitações do aplicativo.

* Os POIs são preenchidos apenas após serem definidos no arquivo de configuração do aplicativo.

   Os POIs não são aplicados a chamadas `trackLocation` históricas enviadas anteriormente.
* As chamadas `trackLocation` permitem o envio de dados de contexto adicionais como as chamadas `trackAction`.

* Quando dois POIs possuem diâmetros sobrepostos, é usado o primeiro POI que contém a localização atual.

   Se seus POIs se sobrepõem, você deve lista os POIs na ordem da mais para a menos granular para garantir que o POI mais granular seja relatado.

