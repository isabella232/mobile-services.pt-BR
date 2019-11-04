---
description: A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.
seo-description: A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.
seo-title: Visualização do Target no iOS
title: Visualização do Target no iOS
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Visualização do Target no iOS{#target-preview-on-ios}

A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.

Para obter mais informações sobre como usar a Visualização do Target, vá para [Visualização do Target para dispositivos móveis](https://docs.adobe.com/content/help/pt-BR/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Para usar a Visualização do Target, é necessário ter a versão 4.14.0 ou posterior do SDK.

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
