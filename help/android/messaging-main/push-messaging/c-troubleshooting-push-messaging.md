---
description: Estas informações ajudam a solucionar problemas de mensagem de push.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: 'Solucionar problemas de mensagens de push  '
topic-fix: Metrics
uuid: 9c4a9371-6691-4a2c-a6c1-b9f901a41599
exl-id: 82b89f56-f43e-4b0d-80c5-5bff4013e5f7
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 100%

---

# Solucionar problemas de mensagens de push {#troubleshooting-push-messaging}

Estas informações ajudam a solucionar problemas de mensagem de push.

## Por que podem ocorrer atrasos no envio das mensagens de push?

Os seguintes tipos de atrasos podem estar associados a mensagens de push para os Mobile Services:

* Aguardar as ocorrências do Analytics

   Todo conjunto de relatórios possui uma configuração que determina quando processar as ocorrências que chegam do Analytics. O padrão é a cada hora. O processamento de ocorrências do Analytics atual pode levar até 30 minutos, embora normalmente demore de 15 a 20 minutos. Por exemplo, um conjunto de relatórios processa ocorrências a cada hora. Se você considerar o tempo de processamento de no máximo 30 minutos, pode levar até 90 minutos para que uma ocorrência recebida esteja disponível para uma mensagem de push. Se um usuário inicializasse o aplicativo às 9h01, a ocorrência apareceria na interface do usuário do Mobile Services como um novo usuário único entre 10h15 e 10h30.

* Aguardar o serviço de push

   O serviço de push (APNS ou FCM) pode não enviar imediatamente a mensagem. Embora incomum, temos visto um atraso de 5 a 10 minutos. Na página Mensagens, é possível verificar se a mensagem de push foi enviada para o serviço de push clicando no link **[!UICONTROL Exibir]** na mensagem. No relatório, o número de envios bem-sucedidos para o serviço por push está listado na coluna **[!UICONTROL Publicado]**.

   >[!TIP]
   >
   >Os serviços de push não garantem que uma mensagem será enviada. Para obter mais informações sobre a confiabilidade dos serviços, consulte a documentação apropriada:
   >
   >* **APNS**: [Qualidade do serviço](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   >* **FCM**: [Tempo de vida de uma mensagem](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)


## Por que as minhas mensagens de push estão sendo cortadas ou não estão expandindo?

Em alguns dispositivos Android, pode ser necessário usar `NotificationCompat.BigTextStyle` ao exibir mensagens.
