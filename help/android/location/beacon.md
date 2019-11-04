---
description: O rastreamento de sinal permite medir e direcionar localizações de micro ao usar o iBeacon e o Bluetooth de baixa energia.
keywords: android;biblioteca;móvel;sdk
seo-description: O rastreamento de sinal permite medir e direcionar localizações de micro ao usar o iBeacon e o Bluetooth de baixa energia.
seo-title: Rastreamento de sinal
solution: Experience Cloud,Analytics
title: Rastreamento de sinal
topic: Desenvolvedor e implementação
uuid: 16c1d267-85f4-4a6a-a6d3-d6ffb0f80b29
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Rastreamento de sinal {#beacon-tracking}

O rastreamento de sinal permite medir e direcionar localizações de micro ao usar o iBeacon e o Bluetooth de baixa energia.

Os seguintes dados de beacon são enviados para o Analytics e o Target quando `trackBeacon` é chamado:

* `a.beacon.uuid` - ProximityUUID do beacon
* `a.beacon.major` - Maior número do sinal (como número de armazenamento)
* `a.beacon.minor` - Menor número do sinal (como número exclusivo em um armazenamento)
* `a.beacon.prox` - Valores de 0 a 3 que representam a proximidade do usuário em relação ao sinal.

Esses valores significam:

* 0 = desconhecido
* 1 = imediato
* 2 = próximo
* 3 = distante

Estes dados de sinal são coletados nas variáveis da solução móvel.

## Rastrear sinais {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto IntelliJ IDEA ou Eclipse* na [Implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Importe a biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Colete a localização do sinal.

   Várias bibliotecas de terceiros estão disponíveis para varrer sinais em Bluetooth de baixa energia, dependendo do fabricante do sinal.
1. Após a obtenção das informações do sinal, use a chamada a seguir para rastrear a localização:

   ```java
   // assumed that the following variables will have been retrieved by the 3rd party beacon library 
   String beaconUUID; 
   String major; 
   String minor; 
   Analytics.BEACON_PROXIMITY proximity;  
   // BEACON_PROXIMITY is an enum available in the SDK. Number 0-3 representing how close the 
   // user is to the beacon. 0 unknown, 1 immediate, 2 near, 3 far.  
   Analytics.trackBeacon(beaconUUID, major, minor, proximity, null);
   ```

1. Quando o usuário sair da proximidade do sinal, limpe o sinal atual:

   ```java
   Analytics.clearBeacon();
   ```

## Enviar dados adicionais {#section_3EBE813E54A24F6FB669B2478B5661F9}

Além dos dados de sinal, é possível enviar dados de contexto adicionais com cada chamada `trackBeacon`:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackBeacon(beaconUUID, major, minor, proximity, cdata);
```

Os valores de dados de contexto devem ser mapeados para variáveis personalizadas no Adobe Mobile Services:

![](assets/map-variable-context-ltv.png)

