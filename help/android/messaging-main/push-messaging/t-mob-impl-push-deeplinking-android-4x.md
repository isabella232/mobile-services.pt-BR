---
description: Depois de configurar o URL de deep linking na interface do usuário do Adobe Mobile Services, este URL estará na carga de envio com a chave adb_deeplink.
title: Implementar mensagens de push com deep linking
uuid: e24f9248-8d48-4e57-84af-3a05b72e2a09
exl-id: ab97db32-d9d2-41ec-aae8-a951c7745df8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 74%

---

# Implementar mensagens por push com deep linking {#implement-push-messaging-with-deep-linking}

Depois de configurar o URL de deep linking na interface do usuário do Adobe Mobile Services, este URL estará na carga de envio com a chave adb_deeplink.

Você pode obter o URL chamando o `remoteMessage.getData().get("adb_deeplink")` no `FirebaseMessagingService`.

>[!TIP]
>
>É possível definir intenções diferentes se a carga tiver ou não um URL de deep linking.

1. Conclua uma das seguintes tarefas:

   * Se o URL do deep linking **estiver** na carga de push, crie uma intenção `ACTION_VIEW` com o URL.

      Quando o usuário clica na mensagem de push, um deep link é acionado.

   * Se o URL de deep linking **não for** na carga de push, crie uma intenção que abrirá uma de suas atividades.

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
