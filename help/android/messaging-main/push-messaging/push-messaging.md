---
description: O Adobe Mobile e o Adobe Mobile SDK permitem enviar mensagens de push para os usuários. Além disso, o SDK permite reportar facilmente os usuários que abriram seu aplicativo depois de clicarem em uma mensagem de push.
seo-description: O Adobe Mobile e o Adobe Mobile SDK permitem enviar mensagens de push para os usuários. Além disso, o SDK permite reportar facilmente os usuários que abriram seu aplicativo depois de clicarem em uma mensagem de push.
seo-title: Mensagens de push
solution: Marketing Cloud,Analytics
title: Mensagens de push
topic: Desenvolvedor e implementação
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
translation-type: tm+mt
source-git-commit: 17cb91a28966cf32f955a2cb724e89ab228de5b8

---


# Push messaging {#push-messaging}

O Adobe Mobile e o Adobe Mobile SDK permitem enviar mensagens de push para os usuários. Além disso, o SDK permite reportar facilmente os usuários que abriram seu aplicativo depois de clicarem em uma mensagem de push.

Para usar as mensagens de push, você **deve** ter a versão 4.6 ou posterior do SDK.

>[!IMPORTANT]
>
>Do not manually set the Experience Cloud ID inside your app. Isso ocasiona na criação de um novo usuário exclusivo que não receberá mensagens de push por causa do status de aceitação. Por exemplo, um usuário que aceitou receber mensagens de push faz logon no seu aplicativo. Depois de fazer logon, se você definir manualmente a ID dentro do aplicativo, um novo usuário único que não aceitou receber mensagens de push é criado. Este novo usuário não receberá suas mensagens de push.
>
>Não há suporte para mover seu aplicativo para um novo conjunto de relatórios. Se você migrar para um novo conjunto de relatórios, sua configuração de push pode ser interrompida e as mensagens podem não ser enviadas.

## Enable push messaging {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>If your app is already set up to use messaging through Firebase Cloud Messaging (FCM), some of the following steps might already be completed.

1. Verify that the `ADBMobileConfig.json` file contains the required settings for push messaging.

   The `"marketingCloud"` object must have its `"org"` property configured for push messaging.

   ```js
   "marketingCloud": { 
     "org": <org-id-string> 
    }
   ```

1. Obtenha a ID/token de registro usando a API do Firebase Cloud Messaging (FCM).

   * Para obter mais informações sobre como configurar o FCM, consulte [Definir um aplicativo do cliente GCM no Android](https://firebase.google.com/docs/cloud-messaging/android/client).
   ```js
   String token = FirebaseInstanceId.getInstance().getToken();
   ```

1. The registration ID/token must be passed to the SDK by using the `Config.setPushIdentifier(final String registrationId)` method.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. Ative o relatório passando sua atividade no método `collectLifecycleData`.

   A seguir, os requisitos para ativar o relatório de click-through de push:

   * In your implementation of `FireBaseMessageService`, the Bundle object that contains the message data, which is passed into the `onMessageReceived` method with the RemoteMessage object, must be added to the Intent that is used to open the target activity on a click-through. Isso pode ser feito usando o `putExtras` método. Para obter mais informações, consulte [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle))).
   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * Na atividade alvo do clickthrough, a atividade deve ser passada pelo SDK com a chamada `collectLifecycleData`.

      Lembre-se das seguintes informações:

      * Use `Config.collectLifecycleData(this)` ou `Config.collectLifecycleData(this, contextData)`.

      * Do **not** use `Config.collectLifecycleData()`.



