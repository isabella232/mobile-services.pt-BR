---
description: The Adobe Experience Platform Identity Service provides a universal visitor ID across Experience Cloud solutions. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.
seo-description: O Adobe Experience Platform Identity Service fornece uma ID de visitante universal nas soluções da Experience Cloud. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.
seo-title: Experience Cloud ID
solution: Marketing Cloud,Analytics
title: Experience Cloud ID
topic: Desenvolvedor e implementação
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

The Adobe Experience Platform Identity Service provides a universal visitor ID across Experience Cloud solutions. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.

>[!TIP]
>
>You do not need to populate the Experience Cloud ID unless you are using the Adobe Experience Platform Identity Service. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**Exige o SDK versão 4.3 ou posterior**

## Enable the Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao seu projeto* em Implementação [principal e Ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe a biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verify that the  files contains the  :`ADBMobileConfig.json``marketingCloud``org`

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   As IDs de organização da Experience Cloud identificam cada empresa cliente na Adobe Experience Cloud e são semelhantes ao seguinte valor: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >You must include .`@AdobeOrg`

   If these values are not present, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Para obter mais informações, consulte Configuração [JSON](/help/ios/getting-started/requirements.md)ADBMobile.

Após a configuração, uma Experience Cloud ID é gerada e incluída em todas as ocorrências. Outras IDs de visitante, como personalizadas e geradas automaticamente, continuarão a ser enviadas com cada ocorrência.
