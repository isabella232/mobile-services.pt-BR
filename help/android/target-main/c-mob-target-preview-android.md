---
description: A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.
title: Visualização do Target no Android
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
exl-id: 69103f3a-9521-4808-8ecd-7b960efca04d
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 74%

---

# Visualização do Target no Android {#target-preview-on-android}

A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.

Para obter mais informações sobre como configurar e usar a Visualização do Target, acesse [Visualização do Target Mobile](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html) no guia do usuário do Adobe Target.

>[!IMPORTANT]
>
>Para usar a Visualização do Target, é necessário ter a versão 4.14.0 ou posterior do SDK.

* **setPreviewRestartDeeplink**

   Define um link direto do aplicativo que será acionado quando as seleções de pré-visualização forem aplicadas no modo de Pré-visualização.

   * Esta é a sintaxe para este método:

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Target.setPreviewRestartDeeplink("myapp://myhost"); 
      ```
