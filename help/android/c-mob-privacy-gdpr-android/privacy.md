---
description: Essas informações o ajudam com a solicitação de exclusão de dados do GDPR.
seo-description: Essas informações o ajudam com a solicitação de exclusão de dados do GDPR.
seo-title: Definir o status de opt-up do usuário
solution: Marketing Cloud, Analytics
title: Definir o status de opt-up do usuário
topic: Desenvolvedor e implementação
uuid: f 8 a 3 e 6 be -44 dd -494 e -9 cda-dbbac 86 d 6772
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Setting the user's opt status{#setting-the-user-s-opt-status}

Essas informações o ajudam com a solicitação de exclusão de dados do GDPR.

>[!IMPORTANT]
>
>Starting with Android SDK 4.15 , setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

É possível controlar se a atividade do Analytics, Target e Audience Manager é permitida em um dispositivo usando as configurações a seguir:

* `privacyDefault` na [configuração JSON do adbmobile](/help/android/configuration/json-config/json-config.md).

   Esta configuração controla a configuração inicial que persiste até que seja alterada no código.

* O `Config.setPrivacyStatus` método.

   Após a configuração de privacidade ser alterada por meio desse método, essa alteração permanece válida até que você a altere novamente ou desinstale e instale o aplicativo novamente. Para obter mais informações sobre os métodos, consulte [Configuração de métodos](/help/android/configuration/methods.md).

A tabela a seguir descreve cada status de privacidade:

* **Aceitar**

   * **Analytics**: as ocorrências são enviadas.
   * **Target**: as solicitações da mbox são enviadas.
   * **Audience Manager**: os sinais e sincronizações de ID são enviados.
   * Value in the JSON Config file: `optedin`
   * Valor em `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_IN`

* **Rejeitar**

   * **Analytics**: as ocorrências são descartadas.
   * **Target**: as solicitações da mbox não são permitidas.
   * **Audience Manager**: os sinais e sincronizações de ID não são permitidos.
   * Value in the JSON config file: `optedout`
   * Valor em `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **Desconhecido**

   * **Analytics**: Se o rastreamento offline **ativado**, as ocorrências são salvas até o status de privacidade ser alterado para opt-in (as ocorrências são enviadas) ou opt-out (as ocorrências são descartadas).

      Se o rastreamento offline <b>não estiver</b> ativado, as ocorrências são descartadas até o status de privacidade ser alterado parar aceitar.
   * **Target**: as solicitações da mbox são enviadas.
   * **Audience Manager**: os sinais e sincronizações de ID são enviados.
   * Value in the JSON config file: `optunknown`
   * Valor em `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_UNKNOWN`

## Exemplos {#section_128AC455EE024193B5D4E5A565B53D00}

```java
public void setOptIn(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptOut(View view) { 
 Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_OUT); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptUnknown(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_UNKNOWN); 
 currentStatus = Config.getPrivacyStatus(); 
}
```

