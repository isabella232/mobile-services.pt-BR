---
description: Estas informações ajudam a configurar a extensão do Android que permite coletar dados do aplicativo Android Wearable.
seo-description: Estas informações ajudam a configurar a extensão do Android que permite coletar dados do aplicativo Android Wearable.
seo-title: Android Wearables  Observações adicionais
solution: Experience Cloud,Analytics
title: Android Wearables  Observações adicionais
topic: Desenvolvedor e implementação
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: observações adicionais{#android-wearables-additional-notes}

Estas informações ajudam a configurar a extensão do Android que permite coletar dados do aplicativo Android Wearable.

* A extensão do Adobe Mobile Android Wearables requer a versão 4.4 (KitKat) ou posterior do Android.
* Há um valor de contexto adicional, `A.RunMode`, que foi adicionado para indicar se os dados são provenientes de uma extensão ou um aplicativo relativo.

   * `RunMode` = `Application`

      A ocorrência vem do aplicativo portátil.

   * `RunMode` = `Extension`

      A ocorrência vem do aplicativo wearable.

* O SDK sincroniza automaticamente o status `aid`/`vid`/`visitor` `service id`/`privacy` do aplicativo portátil para o aplicativo wearable; portanto, não faça uma chamada `setPrivacyStatus`/`setUserIdentifier`/`idSync` do aplicativo wearable.
* [As mensagens no aplicativo](/help/android/messaging-main/messaging/messaging.md), o [Target](/help/android/target-main/target.md) e o [Audience Manager](/help/android/audience-manager/audiencemgmt.md) estão desativados para o aplicativo wearable.

