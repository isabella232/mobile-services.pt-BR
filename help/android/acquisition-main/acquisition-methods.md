---
description: 'Os seguintes métodos de aquisição são fornecidos pela biblioteca do Android '
keywords: android;biblioteca;móvel;sdk
seo-description: 'Os seguintes métodos de aquisição são fornecidos pela biblioteca do Android '
seo-title: Métodos de aquisição
solution: Experience Cloud,Analytics
title: Métodos de aquisição
topic-fix: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
exl-id: 0ce1b8fb-fd45-45de-8f97-e297e4c6529f
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '86'
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
