---
description: Você pode exibir relatórios de mensagens para mensagens no aplicativo e de push.
keywords: mobile
seo-description: Você pode exibir relatórios de mensagens para mensagens no aplicativo e de push.
seo-title: Exibir relatórios de mensagem
solution: Marketing Cloud,Analytics
title: Exibir relatórios de mensagem
topic: Métricas
uuid: 0ac73a81-388f-4dfd-84d5-21b8db4b8c83
translation-type: tm+mt
source-git-commit: 44f531ad140827d563255fad197811185c5337c9

---


# View message reports{#view-message-reports}

Você pode exibir relatórios de mensagens para mensagens no aplicativo e de push.

1. Click ![report icon](assets/icon_report.png) in the **[!UICONTROL Report]** column for a message.
1. (**Optional**) Create a sticky filter for the report or change the time period by clicking the **[!UICONTROL Calendar]** icon.

   Para obter mais informações sobre como criar um filtro fixo, consulte [Adicionar um filtro](/help/using/usage/reports-customize/t-sticky-filter.md)fixo.

>[!TIP]
>
>Dependendo do tipo de mensagem que você está visualizando, o relatório pode variar.

## Mensagens no aplicativo {#section_90B79BA58E8141F78538C187EB1BF8C7}

Se você estiver visualizando os relatórios de uma mensagem no aplicativo, eles serão semelhantes à seguinte ilustração:

![mensagem de relatório](assets/report_message.png)

### Métricas de mensagem no aplicativo

Esta é uma lista das métricas que estão disponíveis para mensagens no aplicativo:

* **[!UICONTROL Impression]**, when a message is triggered.

* **[!UICONTROL Clique até]** quando um usuário pressionar o botão **[!UICONTROL Clicar]** em uma mensagem de alerta ou de tela cheia e quando um usuário abrir o aplicativo a partir de uma notificação local.

* **[!UICONTROL Cancel, when a user presses the Cancel button on an alert or a full-screen message.]******

* **[!UICONTROL Taxa]** de envolvimento, uma métrica calculada do Adobe Analytics e é o resultado do número de click-throughs dividido pelo número de impressões.

## Push messages {#section_BEAFD858CA194185B6F88903446058E9}

Se você estiver visualizando os relatórios de uma mensagem de push, eles serão semelhantes à seguinte ilustração:

![mensagem de push](assets/report_message_push.png)

O gráfico na parte superior exibe o número de usuários que abriram a mensagem.

### Métricas de mensagem de push

Esta é uma lista das métricas disponíveis para mensagens de push:

* **[!UICONTROL Hora]**

   A hora em que a mensagem foi encaminhada para dispositivos do Mobile Services.

* **[!UICONTROL Status]**

   O status da mensagem e os status disponíveis são:

   * **[!UICONTROL Cancelado]**
   * **[!UICONTROL Agendado]**
   * **[!UICONTROL Execução]**
   * **[!UICONTROL Executado]**

* **[!UICONTROL Publicado]**

   The number of device tokens successfully sent to Apple Push Notification Service/Firebase Cloud Messaging (APNS/FCM) for sending the message to the users devices.

* **[!UICONTROL Falha]**

   O número de tokens de dispositivo não enviados com êxito para APNS/FCM. Alguns motivos possíveis para falhas:

   * Uma pushID inválida

   * The push platform (APNS, FCM, and so on) that was given to push to does not exist for the job's application. Por exemplo, a plataforma pode coletar tokens de push do iOS, mas não tem um serviço de APNS configurado.

   * A mensagem pode ter falhado porque o serviço de push não foi configurado corretamente ou o sistema Mobile Services está desativado.
   >[!IMPORTANT]
   >
   >Caso haja um grande número incomum de falhas, verifique a configuração dos serviços de push. Se os serviços de push estiverem configurados corretamente, entre em contato com o Atendimento ao cliente da Adobe.

* **[!UICONTROL Não autorizado]**

   O número de tokens de dispositivo que não são mais válidos para serem enviados para o APNS ou FCM. Isto normalmente significa que o aplicativo foi desinstalado do dispositivo ou o usuário alterou suas configurações de autorização para receber mensagens. O Android e o iOS diferem sobre quando os tokens são considerados como bloqueados. Os tokens do Android são imediatamente mostrados na contagem da lista negra. Os tokens do iOS são inicialmente exibidos como publicados, mas com base no feedback do APNS, são mostrados como bloqueados nas mensagens subsequentes.
