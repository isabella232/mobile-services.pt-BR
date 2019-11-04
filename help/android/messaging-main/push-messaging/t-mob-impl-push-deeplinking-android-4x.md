---
description: Depois de configurar o URL de deep linking na interface do usuário do Adobe Mobile Services, este URL estará na carga de envio com a chave adb_deeplink.
seo-description: Depois de configurar o URL de deep linking na interface do usuário do Adobe Mobile Services, este URL estará na carga de envio com a chave adb_deeplink.
seo-title: Implementar mensagens de push com deep linking
title: Implementar mensagens de push com deep linking
uuid: e24f9248-8d48-4e57-84af-3a05b72e2a09
translation-type: ht
source-git-commit: 13ff2cb549c4b82a4e0285e1c7c6b3f9c1a5bd4b

---


# Implementar mensagens por push com deep linking {#implement-push-messaging-with-deep-linking}

Depois de configurar o URL de deep linking na interface do usuário do Adobe Mobile Services, este URL estará na carga de envio com a chave adb_deeplink.

Você pode obter o URL chamando o `remoteMessage.getData().get("adb_deeplink")` no `FirebaseMessagingService`.

>[!TIP]
>
>É possível definir intenções diferentes se a carga tiver ou não um URL de deep linking.

1. Conclua uma das seguintes tarefas:

   * Se o URL do deep linking **estiver** na carga de push, crie uma intenção `ACTION_VIEW` com o URL.

      Quando o usuário clicar na mensagem de push, um deep link é acionado.

   * Se o URL do deep linking **não estiver** na carga de push, crie uma intensão que abrirá uma das atividades.

## Exemplo

Esta é uma amostra de implementação para a classe estendida a partir de `FirebaseMessagingService`:

```java
public void onMessageReceived(RemoteMessage message) { 
 
       Map<String, String> data = message.getData(); 
       String messageStr = data.get("message"); 
       String deepLink = data.get("adb_deeplink"); 
 
       sendNotification(deepLink, messageStr, data); 
    } 
 
private void sendNotification(String deeplink, String message, Map<String, String> data) { 
       Intent intent; 
 
       if (deeplink!=null) { 
           intent = new Intent(Intent.ACTION_VIEW, Uri.parse(deeplink)); 
       } else { 
           intent = new Intent(this, MainActivity.class); 
       } 
 
       intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP); 
 
       //put the data map into the intent to track clickthroughs 
       Bundle pushData = new Bundle(); 
       Set<String> keySet = data.keySet(); 
       for (String key : keySet) { 
           pushData.putString(key, data.get(key)); 
       } 
 
       intent.putExtras(pushData); 
 
       PendingIntent pendingIntent = PendingIntent.getActivity(this, 0, intent, 
               PendingIntent.FLAG_ONE_SHOT); 
 
       Uri defaultSoundUri= RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION); 
 
       NotificationCompat.Builder notificationBuilder = new NotificationCompat.Builder(this) 
                .setSmallIcon(R.drawable.icon) 
                .setContentTitle("FCM Deep Link Push") 
                .setContentText(message) 
                .setAutoCancel(true) 
                .setSound(defaultSoundUri) 
                .setContentIntent(pendingIntent); 
 
       NotificationManager notificationManager =  
       (NotificationManager)getApplicationContext().getSystemService(Context.NOTIFICATION_SERVICE); 
           notificationManager.notify(0, notificationBuilder.build()); 
       } 
```
