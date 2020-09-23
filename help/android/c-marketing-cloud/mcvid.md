---
description: O Adobe Experience Platform Identity Service fornece uma ID de visitante universal em todas as soluções da Experience Cloud. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.
seo-description: O Adobe Experience Platform Identity Service fornece uma ID de visitante universal em todas as soluções da Experience Cloud. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.
seo-title: Configuração da Experience Cloud ID
solution: Experience Cloud,Analytics
title: Configuração da Experience Cloud ID
topic: Developer and implementation
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 100%

---


# Configuração da Experience Cloud ID {#experience-cloud-id-configuration}

O Adobe Experience Platform Identity Service fornece uma ID de visitante universal em todas as soluções da Experience Cloud. O serviço de ID é exigido pelo Analytics para Target, heartbeat de vídeo e por futuras integrações da Experience Cloud.

>[!TIP]
>
>Não é necessário preencher a ID, a menos que você esteja usando o Adobe Experience Platform Identity Service. Para obter mais informações, consulte [Adobe Experience Platform Identity Service](https://docs.adobe.com/content/help/br/id-service/using/home.html).

>[!IMPORTANT]
>
>Essa funcionalidade exige a versão 4.3 ou posterior do SDK.

Para habilitar a Experience Cloud ID:

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto IntelliJ IDEA ou Eclipse* na [Implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Importe a biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Verifique se o arquivo `ADBMobileConfig.json` contém o `marketingCloudorg`:

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

   Se essas IDs não estiverem configuradas, baixe um arquivo `ADBMobileConfig.json` atualizado do Adobe Mobile Services. Para obter mais informações, consulte [Antes de começar](/help/android/getting-started/requirements.md).

Após a configuração ser concluída, uma ID da Experience Cloud é gerada e incluída em todas as ocorrências. Outras IDs, como personalizadas e geradas automaticamente, continuarão a ser enviadas com cada ocorrência.
