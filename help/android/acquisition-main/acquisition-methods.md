---
description: 'Os seguintes métodos de aquisição são fornecidos pela biblioteca do Android '
keywords: android;library;mobile;sdk
seo-description: 'Os seguintes métodos de aquisição são fornecidos pela biblioteca do Android '
seo-title: Métodos de aquisição
solution: Experience Cloud,Analytics
title: Métodos de aquisição
topic: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 100%

---


# Métodos de aquisição {#acquisition-methods}

Os seguintes métodos de aquisição são fornecidos pela biblioteca do Android:

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
