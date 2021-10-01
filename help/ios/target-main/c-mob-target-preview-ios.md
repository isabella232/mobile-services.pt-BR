---
description: A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.
title: Visualização do Target no iOS
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
exl-id: d5695156-59cd-42c5-b9a3-d8e0ebbb89d0
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 76%

---

# Visualização do Target no iOS{#target-preview-on-ios}

A Visualização do Target permite que você realize tarefas integrais de controle de qualidade para atividades do Target e visualizá-las em seu dispositivo.

Para obter mais informações sobre como configurar e usar a Visualização do Target, consulte [Visualização do Target Mobile](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html) na documentação do Adobe Target.

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
      [ADBMobile targetPreviewRestartDeepLink:@"myapp://myhost"]; 
      ```
