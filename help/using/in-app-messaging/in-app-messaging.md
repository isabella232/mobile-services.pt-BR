---
description: Crie, gerencie e gere relatórios de mensagens no aplicativo e de push.
keywords: mobile
seo-description: Crie, gerencie e gere relatórios de mensagens no aplicativo e de push.
seo-title: Mensagens
solution: Experience Cloud,Analytics
title: Mensagens
topic: Metrics
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 100%

---


# Mensagens {#messaging}

Você pode criar, gerenciar e gerar relatórios de mensagens no aplicativo e por push.

## Nova versão do SDK da Adobe Experience Cloud

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para obter a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o [Launch](https://launch.adobe.com/).
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> Se você estiver usando os SDKs para dispositivos móveis da Adobe Experience Platform com o Adobe Launch, também **deve** instalar a extensão Adobe Analytics Mobile Services para usar os recursos do Adobe Mobile Services, como os Links de aquisição. Para obter mais informações, consulte [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Para obter informações sobre como usar mensagens de push e mensagens no aplicativo com os SDKs da Plataforma de experiências, consulte [Configurar mensagens de push](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) e [Configurar mensagens no aplicativo](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

## Mensagens no aplicativo {#section_8984F4568BC24D32A87429FFCB5184A6}

As mensagens no aplicativo são enviadas aos usuários em tempo real, com base em suas ações e características. As mensagens são acionadas pelos dados do Analytics que já foram rastreados pelo SDK.

Os seguintes tipos de mensagem são aceitos:

* Personalizado e temático
* Tela cheia
* Alertas nativos
* Notificações locais

Para entender como funciona uma mensagem no aplicativo, veja a seguir algumas informações adicionais:

* Mensagens no aplicativo exigem versão a SDK 4.2 ou posterior.
* Você deve especificar quem tem direitos de administrador do aplicativo móvel.

   Esses direitos ativam o acesso aos links de aquisição e às mensagens no aplicativo. Para obter mais informações, consulte [Funções e permissões](/help/using/gs/c-mob-roles-and-permissions.md).
* Depois de aprovada, a mensagem é publicada automaticamente no aplicativo.
* O SDK apresenta a mensagem aos usuários quando os parâmetros da mensagem, como características, acionador e agendamento, são atendidos.
* As mensagens podem conter HTML personalizado ou uma imagem, usando um URL online.

   Uma imagem alternativa ou de backup do conjunto de aplicativos também pode ser especificada para mensagens que são acionadas offline.
* Mensagens ativas e completas oferecem relatórios sobre o total de visualizações, taxa de cliques e muito mais.
* Estão disponíveis modelos para as mensagens personalizadas, o que permite criar facilmente sua própria mensagem no aplicativo.

## Mensagens por push {#section_90555A55BCE7427A90B1577E14BEF51B}

As mensagens de push são enviadas aos usuários que optaram por receber notificações. Você pode direcionar essas mensagens de push aos usuários nos segmentos do Analytics ou em segmentos personalizados. Você pode usar mensagens de push para engajar novamente usuários passivos ou transmitir informações específicas de tempo e localização, uma vez que as mensagens aparecem fora do aplicativo.

Antes de configurar as mensagens por push, consulte [Pré-requisitos para ativar as mensagens por push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md). Após executar essas tarefas, você deve configurar as mensagens de push nos ajustes do seu aplicativo. Para obter mais informações, consulte [Configurar mensagens por push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md).
