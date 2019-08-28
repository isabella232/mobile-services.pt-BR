---
description: O Adobe Experience Platform Identity Service fornece uma ID de visitante universal nas soluções da Experience Cloud. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.
seo-description: O Adobe Experience Platform Identity Service fornece uma ID de visitante universal nas soluções da Experience Cloud. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.
seo-title: Configuração da Experience Cloud ID
solution: Marketing Cloud, Analytics
title: Configuração da Experience Cloud ID
topic: Desenvolvedor e implementação
uuid: 8 ebdf 2 bf-c 581-448 f -9542-f 99 a 19784 fe 7
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID configuration {#experience-cloud-id-configuration}

O Adobe Experience Platform Identity Service fornece uma ID de visitante universal nas soluções da Experience Cloud. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.

>[!TIP]
>
>Não é necessário preencher essa ID a menos que você esteja usando o Adobe Experience Platform Identity Service. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

>[!IMPORTANT]
>
>Essa funcionalidade exige a versão 4.3 ou posterior do SDK.

Para habilitar a Experience Cloud ID:

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o Arquivo de configuração ao projeto intellij IDEA ou Eclipse* na [implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Importe a biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Verifique se `ADBMobileConfig.json` o arquivo contém:`marketingCloudorg`

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
   >Você deve incluir `@AdobeOrg`.

   If these IDs are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Para obter mais informações, consulte [Antes de começar](/help/android/getting-started/requirements.md).

Após a configuração ser concluída, uma Experience Cloud ID é gerada e incluída em todas as ocorrências. Outras IDs, como IDs personalizadas e geradas automaticamente, continuam a ser enviadas com cada ocorrência.
