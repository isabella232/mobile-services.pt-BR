---
description: Você pode exibir relatórios de mensagens para mensagens no aplicativo e de push.
keywords: mobile
seo-description: Você pode exibir relatórios de mensagens para mensagens no aplicativo e de push.
seo-title: Exibir relatórios de mensagem
solution: Marketing Cloud, Analytics
title: Exibir relatórios de mensagem
topic: Métricas
uuid: 0 ac 73 a 81-388 f -4 dfd -84 d 5-21 b 8 db 4 b 8 c 83
translation-type: tm+mt
source-git-commit: 44f531ad140827d563255fad197811185c5337c9

---


# View message reports{#view-message-reports}

Você pode exibir relatórios de mensagens para mensagens no aplicativo e de push.

1. Click ![report icon](assets/icon_report.png) in the **[!UICONTROL Report]** column for a message.
1. (**Optional**) Create a sticky filter for the report or change the time period by clicking the **[!UICONTROL Calendar]** icon.

   Para obter mais informações sobre como criar um filtro fixo, consulte [Adicionar um filtro fixo](/help/using/usage/reports-customize/t-sticky-filter.md).

>[!TIP]
>
>Dependendo do tipo de mensagem exibida, o relatório pode variar.

## Mensagens no aplicativo {#section_90B79BA58E8141F78538C187EB1BF8C7}

Se você estiver visualizando os relatórios de uma mensagem no aplicativo, eles serão semelhantes à seguinte ilustração:

![mensagem de relatório](assets/report_message.png)

### Métricas de mensagens no aplicativo

Esta é uma lista das métricas disponíveis para mensagens no aplicativo:

* **[!UICONTROL Impressão]**, quando uma mensagem é acionada.

* **[!UICONTROL Clique em,]** quando um usuário pressiona o botão **[!UICONTROL Click Through]** em uma mensagem de alerta ou em tela cheia e quando um usuário abre o aplicativo a partir de uma notificação local.

* **[!UICONTROL Cancelar]**, quando um usuário pressiona **[!UICONTROL o botão Cancelar]** em um alerta ou uma mensagem em tela cheia.

* **[!UICONTROL Taxa de envolvimento]**, uma métrica calculada do Adobe Analytics e o resultado do número de cliques dividido pelo número de impressões.

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
   * **[!UICONTROL Programado]**
   * **[!UICONTROL Execução]**
   * **[!UICONTROL Executado]**

* **[!UICONTROL Publicado]**

   O número de tokens do dispositivo enviados com sucesso para o Serviço de notificação por push da Apple/Firebase Cloud Messaging (APNS/FCM) para enviar a mensagem aos dispositivos dos usuários.

* **[!UICONTROL Falha]**

   O número de tokens do dispositivo que não foram enviados com sucesso para o APNS/FCM. Alguns possíveis motivos para falhas:

   * Uma pushID inválida

   * A plataforma de push (APNS, FCM etc.) que foi fornecida para push não existe para o aplicativo do trabalho. Por exemplo, a plataforma pode coletar tokens de push do iOS, mas não tem um serviço de APNS configurado.

   * A mensagem pode ter falhado porque o serviço de push não foi configurado corretamente ou o sistema Mobile Services está desativado.
   >[!IMPORTANT]
   >
   >Caso haja um grande número incomum de falhas, verifique a configuração dos serviços de push. Se os serviços de push estiverem configurados corretamente, entre em contato com o Atendimento ao cliente da Adobe.

* **[!UICONTROL Não autorizado]**

   O número de tokens do dispositivo que não são mais válidos para serem enviados para o APNS ou FCM. Isto normalmente significa que o aplicativo foi desinstalado do dispositivo ou o usuário alterou suas configurações de autorização para receber mensagens. O Android e o iOS diferem sobre quando os tokens são considerados como bloqueados. Os tokens do Android são imediatamente mostrados na contagem da lista negra. Os tokens do iOS são inicialmente exibidos como publicados, mas com base no feedback do APNS, são mostrados como bloqueados nas mensagens subsequentes.
