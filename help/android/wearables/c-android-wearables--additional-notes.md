---
description: Estas informações ajudam a configurar a extensão do Android, que permite coletar dados do aplicativo Android Wearable.
seo-description: Estas informações ajudam a configurar a extensão do Android, que permite coletar dados do aplicativo Android Wearable.
seo-title: Android Wearables  Observações adicionais
solution: Experience Cloud,Analytics
title: Android Wearables  Observações adicionais
topic-fix: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
exl-id: ae8cf2d1-d2b0-456b-bbd3-3980e00bbc84
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 100%

---

# Android Wearables: observações adicionais {#android-wearables-additional-notes}

Estas informações ajudam a configurar a extensão do Android, que permite coletar dados do aplicativo Android Wearable.

* A extensão Adobe Mobile Android Wearables requer o Android versão 4.4 (KitKat) ou superior.
* Há um valor de contexto adicional, `A.RunMode`, que foi adicionado para indicar se os dados são provenientes de uma extensão ou um aplicativo relativo.

   * `RunMode` = `Application`

      A ocorrência vem do aplicativo portátil.

   * `RunMode` =  `Extension`

      A ocorrência vem do aplicativo wearable.

* O SDK sincroniza automaticamente o status `aid`/`vid`/`visitor` `service id`/`privacy` do aplicativo portátil para o aplicativo wearable; portanto, não faça uma chamada `setPrivacyStatus`/`setUserIdentifier`/`idSync` do aplicativo wearable.
* [As mensagens no aplicativo](/help/android/messaging-main/messaging/messaging.md), o [Target](/help/android/target-main/target.md) e o [Audience Manager](/help/android/audience-manager/audiencemgmt.md) estão desativados para o aplicativo wearable.
