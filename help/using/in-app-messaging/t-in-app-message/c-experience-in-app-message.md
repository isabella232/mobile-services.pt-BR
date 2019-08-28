---
description: Configure as opções de experiência para mensagens no aplicativo, incluindo o tipo (tela cheia, alerta ou notificação) e as opções de exibição, texto e botão.
keywords: mobile
seo-description: Configure as opções de experiência para mensagens no aplicativo, incluindo o tipo (tela cheia, alerta ou notificação) e as opções de exibição, texto e botão.
seo-title: Mensagem no aplicativo da experiência
solution: Marketing Cloud, Analytics
title: Mensagem no aplicativo da experiência
topic: Métricas
uuid: 4 c 6 d 6756-47 fb -4 f 1 b -8338-0 b 0 c 9 b 0 fceb 0
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: in-app message {#experience-in-app-message}

Configure as opções de experiência para mensagens no aplicativo, incluindo o tipo (tela cheia, alerta ou notificação) e as opções de exibição, texto e botão.

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. Na página Experiência, digite um nome para a mensagem.
1. Preencha os campos na seção **[!UICONTROL Tipo]:**

   * **[!UICONTROL Tipo]**
Selecione o tipo de mensagem para sua campanha de mensagens no aplicativo:

      * **[!UICONTROL Tela cheia]**
      * **[!UICONTROL Alerta]**
      * **[!UICONTROL Notificação local]**
   * **[!UICONTROL Modelo]**

      Personalize um modelo de mensagem responsiva com tema para o seu conteúdo.

      >[!TIP]
      >
      >This option is displayed only when you select the **[!UICONTROL Full Screen]** message type.

   * **[!UICONTROL Personalizado]**

      Carregue o seu conteúdo HTML personalizado (apenas no modo de tela cheia). Você deve fornecer um link click-through e cancelar.

      1. Clique em **[!UICONTROL Procurar]e baixe um arquivo HTML ou arraste um documento HTML até a janela.**
      1. Clique em **[!UICONTROL Baixar exemplo]para exibir o modelo de conteúdo HTML personalizado.**
      >[!TIP]
      >
      >This option is displayed only when you select the **[!Full Screen]** message type.



1. Preencha os campos na seção **[!UICONTROL Exibir]:**

   * **[!UICONTROL Tema]**
   Selecione um tema para a mensagem.

   * **[!UICONTROL Layout]**

      Selecione o layout do aplicativo na tela do dispositivo.

   * **[!UICONTROL URL da imagem]**

      O URL de uma imagem. If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL Imagem embutida]**

      Caminho para uma imagem no pacote de códigos do seu aplicativo. Esta opção é usada quando não há imagem ou a imagem não está disponível. A imagem talvez não esteja disponível se, por exemplo, o dispositivo estiver offline. If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. Preencha os campos na seção **[!UICONTROL Texto]:**

   * **[!UICONTROL Cabeçalho]**

      Digite o texto para o cabeçalho da mensagem.

   * **[!UICONTROL Conteúdo]**

      Digite o texto para o conteúdo da mensagem.

1. Preencha os campos na seção **[!UICONTROL Botões]:**

   * **[!UICONTROL Botão de Click-Through]**

      Rótulo para o botão de **[!UICONTROL Click-through].** Tocar nesse botão conta como um click-through bem-sucedido. O usuário é redirecionado para o destino.

   * **[!UICONTROL Destino]**

      Selecione um destino específico (como um link da Web, deep link ou link híbrido) para enviar os usuários quando eles clicarem na mensagem. O URL de redirecionamento para um click-through bem-sucedido.

      Este URL pode conter as seguintes informações:

      * `{userId}`, que é substituído pelo identificador do usuário ou está em branco quando o identificador não é definido.
      * `{trackingId}`, que é substituído pelo aid (correlacionado ao *cookie s_ vi* ).
      * `{messageId}`, que é substituído pela ID exclusiva para a mensagem no aplicativo.
      * `{lifetimeValue}`, que é substituído pelo valor da duração ou por zero caso não exista tal valor.
      Veja um exemplo do rastreamento da ID do usuário: `https://www.mysite.com?uid={userId}`.

      If the click-through URL uses `https://` or `https://`, the URL opens in the device browser outside the app. Caso contrário, cada plataforma suportará esquemas que permitem abrir ou consultar o aplicativo se ele tiver sido desenvolvido para oferecer suporte ao esquema personalizado.

      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** or **[!UICONTROL Custom Link]** destination types, the destination type is not tracked. Somente os **[!UICONTROL deep links]são rastreados.** Para obter mais informações, consulte [Destinos](/help/using/acquisition-main/c-create-destinations.md).


1. (Opcional) Visualize o layout de sua mensagem clicando nos ícones a seguir:

   * **[!UICONTROL O resumo]** oculta o painel de visualização.

      Click ![preview](assets/icon_preview.png) to redisplay the preview pane.

   * **[!UICONTROL Alterar a orientação]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). Para relógios, a orientação muda de um round para um quadrado.

   * **[!UICONTROL Visualizar no relógio de um usuário]**

      Para visualizar sua mensagem como ela aparecerá no relógio de um usuário, clique no ícone ![de assistir](assets/icon_watch.png).

   * **[!UICONTROL Visualização no telefone de um usuário]**

      Para visualizar sua mensagem como será exibida no ícone de telefone de clique ![do telefone de um usuário](assets/icon_phone.png).

   * **[!UICONTROL Visualização no tablet de um usuário]**

      Para visualizar a mensagem no tablet de um usuário, clique ![em ícone de tablet](assets/icon_tablet.png).

      Na parte inferior do painel de visualização, você pode ver uma descrição do público-alvo selecionado na etapa anterior. Na parte inferior do painel de visualização também é possível exibir uma descrição do público-alvo selecionado na etapa anterior.

1. Configurar [opções de programação](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md).
