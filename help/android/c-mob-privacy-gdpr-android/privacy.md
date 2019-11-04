---
description: Essas informações o ajudam com a solicitação de exclusão de dados do GDPR.
seo-description: Essas informações o ajudam com a solicitação de exclusão de dados do GDPR.
seo-title: Definição de status de opção do usuário
solution: Experience Cloud,Analytics
title: Definição de status de opção do usuário
topic: Desenvolvedor e implementação
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Definição de status de opção do usuário{#setting-the-user-s-opt-status}

Essas informações o ajudam com a solicitação de exclusão de dados do GDPR.

>[!IMPORTANT]
>
>A partir do Android SDK 4.15, definir o status de privacidade como `unknown` retém as ocorrências do Audience Manager e da Experience Cloud ID.

É possível controlar se a atividade do Analytics, Target e Audience Manager é permitida em um dispositivo usando as configurações a seguir:

* `privacyDefault` na [Configuração JSON do ADBMobile](/help/android/configuration/json-config/json-config.md).

   Esta configuração controla a configuração inicial que persiste até que seja alterada no código.

* O método `Config.setPrivacyStatus`.

   Após a configuração de privacidade ser alterada por meio desse método, essa alteração permanece válida até que você a altere novamente ou desinstale e instale o aplicativo novamente. Para obter mais informações sobre os métodos, consulte [Métodos de configuração](/help/android/configuration/methods.md).

A tabela a seguir descreve cada status de privacidade:

* **Aceitar**

   * **Analytics**: as ocorrências são enviadas.
   * **Target**: as solicitações da mbox são enviadas.
   * **Audience Manager**: os sinais e sincronizações de ID são enviados.
   * Valor no arquivo de configuração JSON: `optedin`
   * Valor em `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_IN`

* **Rejeitar**

   * **Analytics**: as ocorrências são descartadas.
   * **Target**: as solicitações da mbox não são permitidas.
   * **Audience Manager**: os sinais e sincronizações de ID não são permitidos.
   * Valor no arquivo de configuração JSON: `optedout`
   * Valor em `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **Desconhecido**

   * **Analytics**: se o rastreamento offline estiver **ativado**, as ocorrências são salvas até o status de privacidade ser alterado para “aceitar” (as ocorrências são enviadas) ou “recusar” (as ocorrências são descartadas).

      Se o rastreamento offline <b>não estiver</b> ativado, as ocorrências são descartadas até o status de privacidade ser alterado parar aceitar.
   * **Target**: as solicitações da mbox são enviadas.
   * **Audience Manager**: os sinais e sincronizações de ID são enviados.
   * Valor no arquivo de configuração JSON: `optunknown`
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

