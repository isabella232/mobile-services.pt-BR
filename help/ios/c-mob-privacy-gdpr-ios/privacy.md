---
description: Essas informações o ajudam com a solicitação de exclusão de dados do GDPR.
seo-description: Essas informações o ajudam com a solicitação de exclusão de dados do GDPR.
seo-title: Definir status de opção do usuário
solution: Marketing Cloud, Analytics
title: Definir status de opção do usuário
topic: Desenvolvedor e implementação
uuid: 44 a 09 a 25-93 c 6-4 e 1 a-b 69 e -710018 e 8 b 6 c 3
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Setting the user's opt status {#setting-the-user-s-opt-status}

Essas informações o ajudam com a solicitação de exclusão de dados do GDPR.

>[!IMPORTANT]
>
>Starting with Experience Cloud iOS SDKs 4.15, setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

É possível controlar se a atividade do Analytics, do Target e do Audience Manager é permitida em um dispositivo, usando as seguintes configurações:

* `privacyDefault` na [configuração JSON do adbmobile](/help/ios/configuration/json-config/json-config.md).

   Esta configuração contra a configuração inicial que é mantida até sua alteração no código.

* `setPrivacyStatus`.

   Depois de alterar a configuração de privacidade usando este método, a alteração torna-se permanente até ser alterada usando este método ou ao desinstalar e instalar o aplicativo novamente.

   Para obter mais informações sobre os métodos, consulte [Configuração de métodos](/help/ios/configuration/json-config/json-config.md).

Aqui estão informações sobre cada status de privacidade:

* **Aceitar**

   * Analytics: as ocorrências são enviadas.
   * Target: as solicitações da mbox são enviadas.
   * Audience Manager: os sinais e sincronizações de ID são enviados.
   * Value in the JSON config file: `optedin`
   * Valor em `setPrivacyStatus`: `ADBMobilePrivacyStatusOptIn`

* **Rejeitar**

   * Analytics: as ocorrências são descartadas.
   * Target: as solicitações da mbox não são permitidas.
   * Audience Manager: os sinais e sincronizações de ID não são permitidos.
   * Value in the JSON config file: `optedout`
   * Valor em `setPrivacyStatus`: `ADBMobilePrivacyStatusOptOut`

* **Desconhecido**

   * Analytics: se o rastreamento offline **estiver** ativado, as ocorrências são salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas).

      Se o rastreamento offline **não estiver** ativado, as ocorrências são descartadas até o status de privacidade ser alterado parar aceitar.

   * Target: as solicitações da mbox são enviadas.
   * Audience Manager: os sinais e sincronizações de ID são enviados.
   * Value in the JSON config file: `optunknown`
   * Valor em `setPrivacyStatus`: `ADBMobilePrivacyStatusUnknown`

## Exemplos {#section_128AC455EE024193B5D4E5A565B53D00}

```objective-c
- (IBAction) setPrivacyOptIn { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn]; 
} 
- (IBAction) setPrivacyOptOut { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptOut]; 
} 
- (IBAction) setPrivacyOptUnknown { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusUnknown]; 
}
```

