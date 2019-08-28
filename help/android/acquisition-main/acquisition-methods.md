---
description: 'Os seguintes métodos de aquisição são fornecidos pela biblioteca do Android '
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: 'Os seguintes métodos de aquisição são fornecidos pela biblioteca do Android '
seo-title: Métodos de aquisição
solution: Marketing Cloud, Analytics
title: Métodos de aquisição
topic: Desenvolvedor e implementação
uuid: 22 ec 432 f-e 7 ae -4 e 89-be 07-26206 bbeacf 8
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Acquisition methods{#acquisition-methods}

O método de aquisição a seguir é fornecido pela biblioteca do Android:

* **campaignStartForApp**

   Permite aos desenvolvedores iniciar uma campanha de aquisição de aplicativo como se o usuário tivesse clicado em um link. Isso é útil para criar links de aquisição manuais e manipular o redirecionamento da App Store.

   * Esta é a sintaxe para este método:

      ```java
      public static void campaignStartForApp(final String appId final Map<String Object> data); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Acquisition.campaignStartForApp("0652024f-adcd-49f9-9bd7-2552a4564d2f" new 
      HashMap<String Object (){{
           put("custom.key" "value");
      }}); 
      ```
