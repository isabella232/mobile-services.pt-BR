---
description: Estas informações ajudam a solucionar problemas de mensagem de push.
keywords: mobile
seo-description: Estas informações ajudam a solucionar problemas de mensagem de push.
seo-title: Solucionar problemas de mensagens de push
solution: Experience Cloud,Analytics
title: Solucionar problemas de mensagens de push
topic: Metrics
uuid: 87d7dcb6-82a8-46e3-a6ed-7f895a22f2af
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '363'
ht-degree: 100%

---


# Solução de problemas de mensagens por push {#troubleshooting-push-messaging}

Estas informações ajudam a solucionar problemas de mensagem de push.

## Por que podem ocorrer atrasos no envio das mensagens de push?

Os seguintes tipos de atrasos podem estar associados a mensagens de push para os Mobile Services:

* **Aguardar as ocorrências do Analytics**

   Todo conjunto de relatórios possui uma configuração que determina quando processar as ocorrências que chegam do Analytics. O padrão é a cada hora. O processamento de ocorrências do Analytics atual pode levar até 30 minutos, embora normalmente demore de 15 a 20 minutos.

   Por exemplo, um conjunto de relatórios processa ocorrências a cada hora. Se você considerar o tempo de processamento de no máximo 30 minutos, pode levar até 90 minutos para que uma ocorrência recebida esteja disponível para uma mensagem de push. Se um usuário inicializasse o aplicativo às 9h01, a ocorrência apareceria na interface do usuário do Mobile Services como um novo usuário exclusivo entre 10h15 e 10h30.

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


## Como renovo meu Certificado de Serviço Push da Apple?

O envio de mensagens de push requer um Certificado de Serviço de Push válido. Os Mobile Services notificarão quando o certificado estiver perto de expirar ou tiver expirado. Se você receber esta notificação, conclua as seguintes etapas para renovar seu certificado:

1. Clique em **[!UICONTROL Gerenciar configurações do aplicativo]**.
2. Para excluir o certificado atual, navegue até **[!UICONTROL Serviços de push]** e clique em **[!UICONTROL Excluir]**.
3. Configure e teste um novo certificado.

   Para obter mais informações, consulte [Pré-requisitos para ativar mensagens de push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)

4. Clique em **[!UICONTROL Salvar]**.

## Por que não consigo ver minhas mensagens de push em um simulador do iOS?

Os simuladores do iOS não aceitam mensagens de push.
