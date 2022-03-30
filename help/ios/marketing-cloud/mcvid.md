---
description: O Adobe Experience Platform Identity Service fornece uma ID de visitante universal em todas as soluções da Experience Cloud. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.
solution: Experience Cloud Services,Analytics
title: Experience Cloud ID
topic-fix: Developer and implementation
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
exl-id: aa7db365-ad21-431f-bff6-2a6da212dd0c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 91%

---

# Experience Cloud ID {#experience-cloud-id}

O Adobe Experience Platform Identity Service fornece uma ID de visitante universal em todas as soluções da Experience Cloud. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.

>[!TIP]
>
>Não é necessário preencher a Experience Cloud ID, a menos que você esteja usando o serviço de identidade da Adobe Experience Platform. Para obter mais informações, consulte o [Serviço de identidade da Adobe Experience Platform](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=pt-BR) documentação.

## Habilitar a Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

Essas etapas exigem uma versão 4.3 ou posterior do SDK.

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
