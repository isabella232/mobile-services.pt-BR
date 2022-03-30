---
description: 'Os seguintes métodos de aquisição são fornecidos pela biblioteca do Android '
keywords: android;biblioteca;móvel;sdk
solution: Experience Cloud Services,Analytics
title: Métodos de aquisição
topic-fix: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
exl-id: 0ce1b8fb-fd45-45de-8f97-e297e4c6529f
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '74'
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
