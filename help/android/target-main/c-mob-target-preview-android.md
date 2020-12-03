---
description: A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.
seo-description: A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.
seo-title: Visualização do Target no Android
title: Visualização do Target no Android
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 87%

---


# Visualização do Target no Android {#target-preview-on-android}

A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.

For more information on how to set up and use Target Preview, go to [Target Mobile Preview](https://docs.adobe.com/content/help/pt-BR/target/using/implement-target/mobile-apps/target-mobile-preview.html).

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
      Target.setPreviewRestartDeeplink(“myapp://myhost”); 
      ```

