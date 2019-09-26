---
description: Estas informações ajudam a solucionar problemas de mensagem de push.
keywords: mobile
seo-description: Estas informações ajudam a solucionar problemas de mensagem de push.
seo-title: Troubleshoot Push Messaging
solution: Marketing Cloud,Analytics
title: Troubleshoot Push Messaging
topic: Métricas
uuid: 9c4a9371-6691-4a2c-a6c1-b9f901a41599
translation-type: tm+mt
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# Troubleshoot push messaging {#troubleshooting-push-messaging}

Estas informações ajudam a solucionar problemas de mensagem de push.

## Por que podem ocorrer atrasos no envio das mensagens de push?

Os seguintes tipos de atrasos podem estar associados a mensagens de push para os Mobile Services:

* Aguardar as ocorrências do Analytics

   Todo conjunto de relatórios possui uma configuração que determina quando processar as ocorrências que chegam do Analytics. O padrão é a cada hora. O processamento de ocorrências do Analytics atual pode levar até 30 minutos, embora normalmente demore de 15 a 20 minutos. Por exemplo, um conjunto de relatórios processa ocorrências a cada hora. Se você considerar um tempo de processamento de, no máximo, 30 minutos, poderá demorar até 90 minutos para que uma ocorrência recebida esteja disponível para uma mensagem por push. Se um usuário inicializasse o aplicativo às 9h01, a ocorrência apareceria na interface do usuário do Mobile Services como um novo usuário exclusivo entre 10h15 e 10h30.

* Aguardar o serviço de push

   O serviço de push (APNS ou FCM) pode não enviar a mensagem imediatamente. Embora incomum, temos visto um atraso de 5 a 10 minutos. Na página Mensagens, é possível verificar se a mensagem de push foi enviada para o serviço de push clicando no link **Exibir** na mensagem. No relatório, o número de envios bem-sucedidos para o serviço por push está listado na coluna **[!UICONTROL Publicado].**

   >[!TIP]
   >
   >Os serviços de push não garantem que uma mensagem seja enviada.

   Para obter mais informações sobre a confiabilidade dos serviços, consulte a documentação apropriada:

   * **APNS**: [Qualidade do serviço](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   * **FCM**: Duração [de uma mensagem](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)

## Por que as minhas mensagens de push estão sendo cortadas ou não estão expandindo?

Em alguns dispositivos Android, pode ser necessário usar `NotificationCompat.BigTextStyle` ao exibir mensagens.
