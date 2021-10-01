---
description: Você pode anexar arquivos de imagem às notificações do Android. A adição de componentes visuais pode aumentar significativamente a participação do usuário com as notificações por push.
title: Receber notificações por push avançadas
uuid: 4a0340a6-666b-49b6-907a-9afc966dfdba
exl-id: 5776411c-aa0e-4e67-83aa-e78f5d1ed4f7
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 68%

---

# Receber notificações por push avançadas {#receive-rich-push-notifications}

Você pode anexar arquivos de imagem às notificações do Android. A adição de componentes visuais pode aumentar significativamente a participação do usuário com as notificações por push.

## Gerenciar a mensagem de push de entrada detalhada (FCM) {#section_AF1A3BC2312C4E1DA517CC90296C11E2}

Se o aplicativo estiver em primeiro plano, a mensagem de push será gerenciada pelo aplicativo que estende a classe `FirebaseMessagingService` e é declarada no arquivo de manifesto da seguinte forma:

```java
<service
    android:name=".MyFirebaseMessagingService"
    android:exported="false">
    <intent-filter>
        <action android:name="com.google.firebase.MESSAGING_EVENT" />
    </intent-filter>
</service>
```

>[!IMPORTANT]
>
>A classe que contém a implementação `onMessageReceived()` processa os dados recebidos.

Se a mensagem por push tiver um URL de mídia, o URL estará disponível no parâmetro `RemoteMessage` passado para a função `onMessageReceived()`. A chave a ser usada é `attachment-url`, como aparece na seguinte amostra de código:

```java
public class MyFirebaseMessagingService extends FirebaseMessagingService {
        @Override
        public void onMessageReceived(RemoteMessage remoteMessage) {
      Log.d("Remote Message", "RemoteMessage: " + remoteMessage.toString());
            // Check if message contains a data payload.
            if (remoteMessage.getData().size() > 0) {
                Log.d("Remote Message", "RemoteMessage: " + remoteMessage.getData());
                sendNotification(remoteMessage);
            }
    }
 
private void sendNotification(RemoteMessage message) {
        Intent intent = new Intent(this, MainActivity.class);
    intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
    PendingIntent pendingIntent = PendingIntent.getActivity(this, 0 /* Request code */, intent, PendingIntent.FLAG_ONE_SHOT);

     String channelId = getString(R.string.default_notification_channel_id);
     Uri defaultSoundUri = RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION);
     NotificationCompat.Builder notificationBuilder =
                new NotificationCompat.Builder(this, channelId)
                        .setSmallIcon(R.drawable.ic_stat_ic_notification)
                        .setContentTitle(getString(R.string.fcm_message))
                        .setContentText(message.getData().get("body"))
                        .setAutoCancel(true)
                        .setSound(defaultSoundUri)
                        .setContentIntent(pendingIntent);
  
    //Handle image url if present in the push message 
        String attachmentUrl = message.getData().get("attachment-url");
  
    if (attachmentUrl != null) { 
    Bitmap image = getBitmapFromURL(attachmentUrl); 
    if (image != null) { 
      notificationBuilder.setStyle(new        NotificationCompat.BigPictureStyle().bigPicture(image)); 
        } 
        } 

     NotificationManager notificationManager =
              (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);

     // Since android Oreo notification channel is needed.
     if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
        NotificationChannel channel = new NotificationChannel(channelId,
                    "Channel human readable title",
                    NotificationManager.IMPORTANCE_DEFAULT);
            notificationManager.createNotificationChannel(channel);
     }

     notificationManager.notify(0 /* ID of notification */, notificationBuilder.build());
    }
}
```

>[!IMPORTANT]
>
>Ao definir `NotificationCompat.BigPictureStyle`, imagens grandes podem não ser exibidas. Para assegurar que imagens grandes sejam sempre exibidas, defina o `Notification.BigPictureStyle` nativo.

## Amostra de notificação por push avançada {#section_6819316BEDDE45108413B541CA2BB2DC}

Na seguinte imagem, há um exemplo de uma notificação por push detalhada:

![](assets/rich-push-notification_example.png)

Para obter mais informações sobre notificações por push avançadas com o Android, consulte [Engajar com notificações avançadas](https://developer.android.com/distribute/best-practices/engage/rich-notifications.html).
