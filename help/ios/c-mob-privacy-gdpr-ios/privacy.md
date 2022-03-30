---
description: Essas informações o ajudam com a solicitação de exclusão de dados do GDPR.
solution: Experience Cloud Services,Analytics
title: Definição de status de opção do usuário
topic-fix: Developer and implementation
uuid: 44a09a25-93c6-4e1a-b69e-710018e8b6c3
exl-id: 8fd30bea-6316-46ac-9787-8ca594545d1b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 100%

---

# Definição de status de opção do usuário {#setting-the-user-s-opt-status}

Essas informações o ajudam com a solicitação de exclusão de dados do GDPR.

>[!IMPORTANT]
>
>A partir do Experience Cloud iOS SDKs 4.15, definir o status de privacidade como `unknown` retém as ocorrências do Audience Manager e da Experience Cloud ID.

É possível controlar se a atividade do Analytics, do Target e do Audience Manager é permitida em um dispositivo, usando as seguintes configurações:

* `privacyDefault` na [Configuração JSON do ADBMobile](/help/ios/configuration/json-config/json-config.md).

   Esta configuração contra a configuração inicial que é mantida até sua alteração no código.

* `setPrivacyStatus`.

   Depois de alterar a configuração de privacidade usando este método, a alteração torna-se permanente até ser alterada usando este método ou ao desinstalar e instalar o aplicativo novamente.

   Para obter mais informações sobre os métodos, consulte  [Métodos de configuração](/help/ios/configuration/json-config/json-config.md).

Veja a seguir informações sobre cada status de privacidade:

* **Aceitar**

   * Analytics: as ocorrências são enviadas.
   * Target: as solicitações da mbox são enviadas.
   * Audience Manager: as sincronizações de ID e os sinais são enviados.
   * Valor no arquivo de configuração JSON: `optedin`
   * Valor em `setPrivacyStatus`: `ADBMobilePrivacyStatusOptIn`

* **Rejeitar**

   * Analytics: as ocorrências são descartadas.
   * Target: as solicitações da mbox não são permitidas.
   * Audience Manager: as sincronizações de ID e os sinais não são permitidos.
   * Valor no arquivo de configuração JSON: `optedout`
   * Valor em `setPrivacyStatus`: `ADBMobilePrivacyStatusOptOut`

* **Desconhecido**

   * Analytics: se o rastreamento offline **estiver** ativado, as ocorrências são salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas).

      Se o rastreamento offline **não estiver** ativado, as ocorrências são descartadas até o status de privacidade ser alterado parar aceitar.

   * Target: as solicitações da mbox são enviadas.
   * Audience Manager: as sincronizações de ID e os sinais são enviados.
   * Valor no arquivo de configuração JSON: `optunknown`
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
