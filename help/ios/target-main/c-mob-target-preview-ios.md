---
description: A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.
seo-description: A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.
seo-title: Visualização do Target no iOS
title: Visualização do Target no iOS
uuid: d 92867 a 4-0569-4732-a 928-28 f 9 e 2 f 8 b 21 e
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Visualização do Target no iOS{#target-preview-on-ios}

A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.

For more information on how to set up and use Target Preview, see [Target Mobile Preview](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Para usar a Visualização do Target, você precisa da versão 4.14.0 ou posterior do SDK.

## Método de visualização do Target

* **setPreviewRestartDeeplink**

   Define um deeplink de aplicativo que será acionado quando seleções de visualização são aplicadas no modo de Visualização.

   * Esta é a sintaxe para este método:

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
