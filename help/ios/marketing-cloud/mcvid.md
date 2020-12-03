---
description: O Adobe Experience Platform Identity Service fornece uma ID de visitante universal em todas as soluções da Experience Cloud. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.
seo-description: O Adobe Experience Platform Identity Service fornece uma ID de visitante universal em todas as soluções da Experience Cloud. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.
seo-title: Experience Cloud ID
solution: Experience Cloud,Analytics
title: Experience Cloud ID
topic: Developer and implementation
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 100%

---


# Experience Cloud ID {#experience-cloud-id}

O Adobe Experience Platform Identity Service fornece uma ID de visitante universal em todas as soluções da Experience Cloud. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.

>[!TIP]
>
>Não é necessário preencher a Experience Cloud ID, a menos que você esteja usando o serviço de identidade da Adobe Experience Platform. Para obter mais informações, consulte [Adobe Experience Platform Identity Service](https://docs.adobe.com/content/help/pt-BR/id-service/using/home.html).

**Exige o SDK versão 4.3 ou posterior**

## Habilitar a Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao seu projeto* em [Implementação principal e ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe a biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verifique se os arquivos `ADBMobileConfig.json` contêm `marketingCloud` `org`:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   As IDs de organização da Experience Cloud identificam cada empresa cliente na Adobe Experience Cloud e são semelhantes ao seguinte valor: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >Você deve incluir `@AdobeOrg`.

   Se esses valores não estiverem presentes, baixe um arquivo `ADBMobileConfig.json` atualizado do Adobe Mobile Services. Para obter mais informações, consulte [Configuração JSON do ADBMobile](/help/ios/getting-started/requirements.md).

Após a configuração, uma ID da Experience Cloud é gerada e incluída em todas as ocorrências. Outras IDs de visitante, como personalizadas e geradas automaticamente, continuarão a ser enviadas com cada ocorrência.
