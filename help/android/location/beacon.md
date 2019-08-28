---
description: O rastreamento de sinal permite medir e direcionar localizações de micro ao usar o iBeacon e o Bluetooth de baixa energia.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: O rastreamento de sinal permite medir e direcionar localizações de micro ao usar o iBeacon e o Bluetooth de baixa energia.
seo-title: Rastreamento de sinal
solution: Marketing Cloud, Analytics
title: Rastreamento de sinal
topic: Desenvolvedor e implementação
uuid: 16 c 1 d 267-85 f 4-4 a 6 a-a 6 d 3-d 6 ffb 0 f 80 b 29
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Rastreamento de sinal {#beacon-tracking}

O rastreamento de sinal permite medir e direcionar localizações de micro ao usar o iBeacon e o Bluetooth de baixa energia.

Os seguintes dados de beacon são enviados para o Analytics e o Target quando `trackBeacon` é chamado:

* `a.beacon.uuid` - Proximityuuid do beacon
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

   Para obter mais informações, consulte *Adicionar o SDK e o Arquivo de configuração ao projeto intellij IDEA ou Eclipse* na [implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).

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

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Além dos dados de sinal, é possível enviar dados de contexto adicionais com cada chamada `trackBeacon`:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackBeacon(beaconUUID, major, minor, proximity, cdata);
```

Os valores de dados de contexto devem ser mapeados para variáveis personalizadas nos Adobe Mobile Services:

![](assets/map-variable-context-ltv.png)

