---
description: A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.
seo-description: A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.
seo-title: Visualização do Target no iOS
title: Visualização do Target no iOS
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 100%

---


# Visualização do Target no iOS {#target-preview-on-ios}

A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.

Para obter mais informações sobre como usar a Visualização do Target, vá para [Visualização do Target para dispositivos móveis](https://docs.adobe.com/content/help/pt-BR/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Para usar a Visualização do Target, é necessário ter a versão 4.14.0 ou posterior do SDK.

## Método de visualização do Target

* **setPreviewRestartDeeplink**

   Define um link direto do aplicativo que será acionado quando as seleções de pré-visualização forem aplicadas no modo de Pré-visualização.

   * Esta é a sintaxe para este método:

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
