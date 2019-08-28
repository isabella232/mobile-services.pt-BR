---
description: Estas informações ajudam a solucionar problemas de mensagem de push.
keywords: mobile
seo-description: Estas informações ajudam a solucionar problemas de mensagem de push.
seo-title: Solucionar problemas de mensagens de push
solution: Marketing Cloud, Analytics
title: Solucionar problemas de mensagens de push
topic: Métricas
uuid: 87 d 7 dcb 6-82 a 8-46 e 3-a 6 ed -7 f 895 a 22 f 2 af
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Troubleshooting push messaging {#troubleshooting-push-messaging}

Estas informações ajudam a solucionar problemas de mensagem de push.

## Por que podem ocorrer atrasos no envio das mensagens de push?

Os seguintes tipos de atrasos podem estar associados a mensagens de push para os Mobile Services:

* **Aguardar as ocorrências do Analytics**

   Todo conjunto de relatórios possui uma configuração que determina quando processar as ocorrências que chegam do Analytics. O padrão é a cada hora. O processamento de ocorrências do Analytics atual pode levar até 30 minutos, embora normalmente demore de 15 a 20 minutos.

   Por exemplo, um conjunto de relatórios processa ocorrências a cada hora. Se você considerar um tempo de processamento de, no máximo, 30 minutos, poderá demorar até 90 minutos para que uma ocorrência recebida esteja disponível para uma mensagem por push. Se um usuário inicializasse o aplicativo às 9h01, a ocorrência apareceria na interface do usuário do Mobile Services como um novo usuário exclusivo entre 10h15 e 10h30.

* **Aguardar o serviço de push**

   O serviço de push (APNS ou GCM) pode não enviar imediatamente a mensagem. Embora incomum, temos visto um atraso de 5 a 10 minutos. Na página Mensagens, é possível verificar se a mensagem de push foi enviada para o serviço de push clicando no link Exibir na mensagem. No relatório, o número de envios bem-sucedidos para o serviço por push está listado na coluna Publicado.

   >[!TIP]
   >
   >Os serviços de push não garantem que uma mensagem será enviada. Para obter mais informações sobre a confiabilidade dos serviços, consulte a documentação apropriada:
   >
   >* **APNS**: [Qualidade do serviço](https://developer.apple.com/documentation/usernotifications)
      >
      >
   * **GCM**: [Tempo de vida de uma mensagem](https://developers.google.com/cloud-messaging/concept-options)


## Como faço para renovar o meu Certificado de serviço por push da Apple?

O envio de mensagens de push exige um certificado de serviço por push válido. Os Mobile Services notificarão quando o certificado estiver perto de expirar ou tiver expirado. Se você receber esta notificação, conclua as seguintes etapas para renovar seu certificado:

1. Clique em **[!UICONTROL Gerenciar configurações do aplicativo]**.
2. Para excluir o certificado atual, navegue até **[!UICONTROL Serviços de push]** e clique em **[!UICONTROL Excluir]**.
3. Configure e teste um novo certificado.

   Para obter mais informações, consulte [Pré-requisitos para ativar mensagens de push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)

4. Clique em **[!UICONTROL Salvar]**.

## Por que não consigo ver minhas mensagens de push em um simulador do iOS?

Os simuladores iOS não suportam envio de mensagens de push.
