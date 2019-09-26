---
description: Estas informações ajudam a configurar a extensão do Android que permite coletar dados do aplicativo Android Wearable.
seo-description: Estas informações ajudam a configurar a extensão do Android que permite coletar dados do aplicativo Android Wearable.
seo-title: Android Wearables  Additional Notes
solution: Marketing Cloud,Analytics
title: Notas adicionais do Android Wearables
topic: Desenvolvedor e implementação
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: additional notes{#android-wearables-additional-notes}

Estas informações ajudam a configurar a extensão do Android que permite coletar dados do aplicativo Android Wearable.

* A extensão do Adobe Mobile Android Wearables requer a versão 4.4 (KitKat) ou posterior do Android.
* Há um valor de contexto adicional, `A.RunMode`, que foi adicionado para indicar se os dados são provenientes de uma extensão ou um aplicativo relativo.

   * `RunMode` = `Application`

      A ocorrência vem do aplicativo portátil.

   * `RunMode` = `Extension`

      A ocorrência vem do aplicativo wearable.

* The SDK automatically syncs the `aid`/`vid`/`visitor` `service id`/`privacy` status from the handheld app to the wearable app, so do not call `setPrivacyStatus`/`setUserIdentifier`/`idSync` from the wearable app.
* [As mensagens](/help/android/messaging-main/messaging/messaging.md)no aplicativo, o [Target](/help/android/target-main/target.md)e o [Audience Manager](/help/android/audience-manager/audiencemgmt.md) estão desativados para o aplicativo wearable.

