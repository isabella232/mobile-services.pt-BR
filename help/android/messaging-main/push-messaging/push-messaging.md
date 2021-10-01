---
description: O Adobe Mobile e o SDK do Adobe Mobile permitem enviar mensagens de push para seus usuários. O SDK também permite reportar com facilidade usuários que abriram seu aplicativo depois de clicar em uma mensagem de push.
solution: Experience Cloud,Analytics
title: Mensagens por push
topic-fix: Developer and implementation
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
exl-id: 4472e0b9-1d00-4e1a-8653-f3976b74c078
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 100%

---

# Mensagens por push {#push-messaging}

O Adobe Mobile e o SDK do Adobe Mobile permitem enviar mensagens de push para seus usuários. O SDK também permite reportar com facilidade usuários que abriram seu aplicativo depois de clicar em uma mensagem de push.

Para usar mensagens de push, você **deve** ter o SDK versão 4.6 ou posterior.

>[!IMPORTANT]
>
>Não defina a Experience Cloud ID manualmente dentro do aplicativo. Isso resulta na criação de um novo usuário único que não receberá mensagens de push devido ao seu status de aceitação. Por exemplo, um usuário aceitou receber mensagens de push para fazer logon no aplicativo. Depois de fazer logon, se você definir manualmente a ID dentro do aplicativo, um novo usuário único que não optou por receber mensagens de push será criado. Este novo usuário não receberá suas mensagens de push.
>
>Não é possível mover seu aplicativo para um novo conjunto de relatórios. Se você migrar para um novo conjunto de relatórios, sua configuração de push pode ser interrompida e as mensagens podem não ser enviadas.

## Ativar mensagens por push {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>Se o aplicativo já estiver definido para usar mensagens via Firebase Cloud Messaging (FCM), algumas das etapas a seguir podem já estar completas.

1. Verifique se o arquivo `ADBMobileConfig.json` contém as configurações exigidas para mensagens de push.

   O objeto `"marketingCloud"` deve ter sua propriedade `"org"` configurada para mensagens de push.

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

1. A ID/token de registro deve ser passada para o SDK usando o método `Config.setPushIdentifier(final String registrationId)`.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. Ative o relatório passando sua atividade no método `collectLifecycleData`.

   A seguir, os requisitos para ativar o relatório de click-through de push:

   * Na implementação do `FireBaseMessageService`, o objeto Pacote, que contém os dados de mensagem passados para o método `onMessageReceived` com o objeto RemoteMessage, devem ser adicionados à Finalidade usada para abrir a atividade alvo em um click-through. Isso pode ser feito usando o método `putExtras`. Para obter mais informações, consulte [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle))).

   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * Na atividade alvo do clickthrough, a atividade deve ser passada pelo SDK com a chamada `collectLifecycleData`.

      Lembre-se das seguintes informações:

      * Use `Config.collectLifecycleData(this)` ou `Config.collectLifecycleData(this, contextData)`.

      * **Não** use `Config.collectLifecycleData()`.
