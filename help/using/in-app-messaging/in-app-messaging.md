---
description: Crie, gerencie e gere relatórios de mensagens no aplicativo e de push.
keywords: mobile
seo-description: Crie, gerencie e gere relatórios de mensagens no aplicativo e de push.
seo-title: Mensagens
solution: Marketing Cloud, Analytics
title: Mensagens
topic: Métricas
uuid: e 32 d 3 e 35-2 d 09-4 ddf -8919-75 dc 895 abcb 3
translation-type: tm+mt
source-git-commit: 3b744229b3fc288363be74c3c4adcd71ecc4fad4

---


# Mensagens {#messaging}

Você pode criar, gerenciar e gerar relatórios sobre mensagens no aplicativo e de push.

## Nova versão do SDK da Adobe Experience Cloud

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para começar, acesse o [Launch](https://launch.adobe.com/).
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as Acquisition links. Para obter mais informações, consulte [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Para obter informações sobre como usar mensagens de push e mensagens no aplicativo com oso SDKs da Plataforma de experiências, consulte [Configurar mensagens de push](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) e [Configurar mensagensno aplicativo](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

## Mensagens no aplicativo {#section_8984F4568BC24D32A87429FFCB5184A6}

As mensagens no aplicativo são enviadas aos usuários em tempo real, com base em suas ações e características. As mensagens são acionadas pelos dados do Analytics que já foram rastreados pelo SDK.

Os seguintes tipos de mensagens são suportados:

* Personalizado e temático.
* Tela cheia
* Alertas nativos
* Notificações locais

Para ajudá-lo a entender como as mensagens no aplicativo funcionam, estas são algumas informações adicionais:

* As mensagens no aplicativo exigem a versão 4.2 ou posterior do SDK.
* Você deve especificar quem tem os direitos de administrador do aplicativo móvel.

   Esses direitos permitem o acesso aos links de aquisição e às mensagens no aplicativo. Para obter mais informações, consulte [Funções e permissões](/help/using/gs/c-mob-roles-and-permissions.md).
* Após ser aprovada, a mensagem é publicada automaticamente no aplicativo.
* O SDK apresenta a mensagem aos usuários quando seus parâmetros (como características, acionador e agendamento) são cumpridos.
* As mensagens podem conter código HTML personalizado ou uma imagem, usando um URL online.

   Uma imagem alternativa ou de backup do pacote do aplicativo também pode ser especificada para mensagens acionadas de forma offline.
* Mensagens ativas e completas oferecem relatórios sobre o total de visualizações, taxa de cliques e muito mais.
* Estão disponíveis modelos para as mensagens personalizadas, o que permite criar facilmente sua própria mensagem no aplicativo.

## Push messages {#section_90555A55BCE7427A90B1577E14BEF51B}

As mensagens de push são enviadas aos usuários que optaram por receber notificações. Você pode direcionar essas mensagens de push aos usuários nos segmentos do Analytics ou em segmentos personalizados. Você pode usar mensagens de push para engajar novamente usuários passivos ou transmitir informações específicas de tempo e localização, uma vez que as mensagens aparecem fora do aplicativo.

Antes de configurar as mensagens de push, consulte [Pré-requisitos para ativar as mensagens de push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md). Após executar essas tarefas, você deve configurar as mensagens de push nos ajustes do seu aplicativo. For more information, see [Configure push messaging](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md).
