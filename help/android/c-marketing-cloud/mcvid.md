---
description: O Adobe Experience Platform Identity Service fornece uma ID de visitante universal nas soluções da Experience Cloud. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.
seo-description: The Adobe Experience Platform Identity Service provides a universal visitor ID across Experience Cloud solutions. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.
seo-title: Configuração da Experience Cloud ID
solution: Marketing Cloud,Analytics
title: Configuração da Experience Cloud ID
topic: Desenvolvedor e implementação
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID configuration {#experience-cloud-id-configuration}

O Adobe Experience Platform Identity Service fornece uma ID de visitante universal nas soluções da Experience Cloud. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.

>[!TIP]
>
>Não é necessário preencher essa ID a menos que esteja usando o Adobe Experience Platform Identity Service. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

>[!IMPORTANT]
>
>This functionality requires SDK version 4.3 or later.

Para habilitar a Experience Cloud ID:

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   For more information, see Add the SDK and Config File to your IntelliJ IDEA or Eclipse Project in Core implementation and lifecycle.**[](/help/android/getting-started/dev-qs.md)

1. Importe a biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Verify that the  file contains the :`ADBMobileConfig.json``marketingCloudorg`

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   As IDs de organização da Experience Cloud identificam cada empresa cliente na Adobe Experience Cloud e são semelhantes ao seguinte valor:

   ```js
   016D5C175213CCA80A490D05@AdobeOrg`
   ```

   >[!IMPORTANT]
   >
   >You must include .`@AdobeOrg`

   If these IDs are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Para obter mais informações, consulte [Antes de começar](/help/android/getting-started/requirements.md).

Após a configuração ser concluída, uma Experience Cloud ID é gerada e incluída em todas as ocorrências. Outras IDs, como IDs personalizadas e geradas automaticamente, continuam a ser enviadas com cada ocorrência.
