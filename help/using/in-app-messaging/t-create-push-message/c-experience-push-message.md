---
description: Você pode configurar as opções de experiência para mensagens de push e mensagens de push avançadas, incluindo as opções de nome, texto da mensagem e destino. Você também pode configurar opções avançadas, incluindo opções de carga e opções personalizadas para dispositivos iOS.
keywords: dispositivos móveis
seo-description: Você pode configurar as opções de experiência para mensagens de push e mensagens de push avançadas, incluindo as opções de nome, texto da mensagem e destino. Você também pode configurar opções avançadas, incluindo opções de carga e opções personalizadas para dispositivos iOS.
seo-title: Experiência  mensagem por push
solution: Experience Cloud,Analytics
title: Experiência  mensagem por push
topic-fix: Metrics
uuid: 1a8baf3e-9fea-452c-b0fc-4ba8ac270861
exl-id: 9158487e-6ac5-4f17-a8ff-15de0360ab60
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 100%

---

# Experiência: mensagem por push {#experience-push-message}

Você pode configurar as opções de experiência para mensagens de push e mensagens de push avançadas, incluindo as opções de nome, texto da mensagem e destino. Você também pode configurar opções avançadas, incluindo opções de carga e opções personalizadas para dispositivos iOS.

1. Na página Público de uma nova mensagem por push, clique em **[!UICONTROL Experiência]**.

   ![tela de mensagem por push da experiência](assets/experience-push-message.png)

1. Digite um nome para esta mensagem.
1. Digite as informações nos seguintes campos na seção **[!UICONTROL Mensagem]**:

   * **[!UICONTROL Conteúdo]**

      Especifique o texto da mensagem. É possível usar até 140 caracteres.

   * **[!UICONTROL URL de mídia]**

      Digite o URL do arquivo de mídia que você planeja usar na mensagem de notificação por push. Para saber quais são os requisitos para usar notificações por push avançadas, consulte *Requisitos para notificações por push avançadas* abaixo.

      >[!IMPORTANT]
      >
      >Para exibir uma imagem ou um vídeo em uma notificação por push, lembre-se do seguinte:
      > * Os dados `attachment-url` são tratados na carga do push.
      > * O URL da mídia deve ser capaz de lidar com picos de solicitações.


   * **[!UICONTROL Destino]**

      Selecione um destino específico (como um link da Web, deep link ou link híbrido) para enviar os usuários quando eles clicarem na mensagem. Para obter mais informações, consulte [Destinos](/help/using/acquisition-main/c-create-destinations.md).

      >[!TIP]
      >
      >Se você usar os tipos de destino * **[!UICONTROL Link da Web]** ou **[!UICONTROL Link personalizado]**, o tipo de destino não será rastreado. Somente os **[!UICONTROL deep links]** são rastreados.

## Requisitos para notificações por push avançadas

Estes são os requisitos para enviar notificações por push avançadas:

* **Versões suportadas**

   As notificações por push avançadas são suportadas nas seguintes versões:
   * Android 4.1.0 ou posterior
   * iOS 10 ou posterior

      >[!IMPORTANT]
      >
      >Lembre-se das seguintes informações:
      >* As mensagens por push avançadas enviadas para versões anteriores ainda serão enviadas, mas somente o texto será exibido.
      >* Ainda não há suporte para relógio no momento.


* **Formatos de arquivo**

   Estes formatos de arquivos são aceitos:
   * Imagens: JPG e PNG
   * Animações (somente iOS): GIF
   * Vídeos (somente iOS): MP4

* **Formatos de URL**
   * Somente HTTPS

* **Dimensionamento**
   * As imagens devem estar em um formato 2:1 ou serão cortadas.

Para obter mais informações sobre como configurar notificações por push avançadas, consulte o seguinte conteúdo:

* [Receber notificações por push no Android](/help/android/messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
* [Receber notificações por push avançadas no iOS](/help/ios/messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)

Para configurar uma mensagem por push na página Experiência:

1. (**Opcional**) Clique no link **[!UICONTROL Mostrar opções avançadas]** para configurar opções adicionais:

   * **[!UICONTROL Carga: dados]**

      Forneça uma carga de push personalizada no JSON que será enviada para o aplicativo por meio de uma notificação por push ou local. O limite para Android e iOS é 4 KB.

   * **[!UICONTROL Opções da Apple: categoria]**

      Forneça uma categoria para as notificações locais e por push. Para obter mais informações, consulte [Gerenciamento do suporte a notificações do seu aplicativo](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW9) na *Biblioteca de desenvolvedores do iOS*.

   * **[!UICONTROL Opções da Apple: som]**

      Forneça o nome do arquivo de som, localizado em seu pacote de aplicativos, que deseja reproduzir. Se não estiver definido, um som de alerta padrão é reproduzido. Para obter mais informações, consulte [Gerenciamento do suporte a notificações do seu aplicativo](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW10) na *Biblioteca de desenvolvedores do iOS*.

   * **[!UICONTROL Opções da Apple: conteúdo disponível]**

      Selecione esta opção para que, quando a mensagem chegar, o iOS ative o seu aplicativo em segundo plano e permita que ele execute o código com base na carga da mensagem. Para obter mais informações, consulte [Serviço de notificações por push da Apple](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1) na *Biblioteca de Desenvolvedores iOS*.

1. (Opcional) Visualize o layout de sua mensagem clicando nos ícones a seguir:

   * **[!UICONTROL x Resumo]**

      Oculta o painel de visualização. Clique em ![visualizar](assets/icon_preview.png) para exibir o painel de visualização novamente.

   * **[!UICONTROL Alterar a orientação]**

      Para alterar a orientação da visualização do modo retrato para paisagem, clique em ![orientação](assets/icon_orientation.png). Nos relógios, a orientação muda o mostrador do relógio de redondo para quadrado.

   * **[!UICONTROL Visualizar no relógio de um usuário]**

      Para visualizar sua mensagem como ela aparecerá nos relógios de um usuário, clique no ![ícone de observação](assets/icon_watch.png).

   * **[!UICONTROL Visualizar no celular de um usuário]**

      Para visualizar sua mensagem como ela aparecerá nos celulares dos usuários, clique no ![ícone de telefone](assets/icon_phone.png).

   * **[!UICONTROL Visualizar no tablet de um usuário]**

      Para visualizar sua mensagem no tablet de um usuário, clique no ![ícone do tablet](assets/icon_tablet.png).
   Na parte inferior do painel de visualização, você pode ver uma descrição do público-alvo selecionado na etapa anterior.

1. (**Opcional**) Clique em **[!UICONTROL Testar]** para encaminhar sua mensagem a dispositivos especificados para fins de testes.
1. Selecione o serviço e digite os tokens de push para pelo menos um dispositivo para o qual você deseja enviar a mensagem.

   Especifique os tokens em uma lista separada por vírgulas para encaminhar a mensagem para mais de um dispositivo.

1. Configure as opções de agendamento para a mensagem.

   Para obter mais informações, consulte [Programar: mensagem por push](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).
