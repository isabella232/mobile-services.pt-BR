---
description: A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.
seo-description: A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.
seo-title: Visualização do Target no Android
title: Visualização do Target no Android
uuid: f 3 c 82 d 64-009 c -4929-a 5 e 6-3677 b 2977889
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# Visualização do Target no Android {#target-preview-on-android}

A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.

Para obter mais informações sobre como usar a Visualização do Target, consulte [Visualização do Target para dispositivos móveis](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Para usar a Visualização do Target, você precisa da versão 4.14.0 ou posterior do SDK.

* **setPreviewRestartDeeplink**

   Define um deeplink de aplicativo que será acionado quando seleções de visualização são aplicadas no modo de Visualização.

   * Esta é a sintaxe para este método:

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Target.setPreviewRestartDeeplink(“myapp://myhost”); 
      ```

