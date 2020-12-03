---
description: Configure as opções de experiência para mensagens no aplicativo, incluindo o tipo (tela cheia, alerta ou notificação) e as opções de exibição, texto e botão.
keywords: mobile
seo-description: Configure as opções de experiência para mensagens no aplicativo, incluindo o tipo (tela cheia, alerta ou notificação) e as opções de exibição, texto e botão.
seo-title: Experiência  Mensagem no aplicativo
solution: Experience Cloud,Analytics
title: Experiência  Mensagem no aplicativo
topic: Metrics
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 100%

---


# Experiência: mensagem no aplicativo {#experience-in-app-message}

Configure as opções de experiência para mensagens no aplicativo, incluindo o tipo (tela cheia, alerta ou notificação) e as opções de exibição, texto e botão.

1. No seu aplicativo, clique em **[!UICONTROL Mensagens]** > **[!UICONTROL Gerenciar mensagens]** > **[!UICONTROL Criar mensagem]** > **[!UICONTROL Criar mensagem no aplicativo]**.
1. Na página Experiência, digite um nome para a mensagem.
1. Preencha os campos na seção **[!UICONTROL Tipo]**:

   * **[!UICONTROL Tipo]**
Selecione o tipo de mensagem para sua campanha de mensagens no aplicativo:

      * **[!UICONTROL Tela cheia]**
      * **[!UICONTROL Alerta]**
      * **[!UICONTROL Notificação local]**
   * **[!UICONTROL Modelo]**

      Personalize um modelo de mensagem responsiva com tema para o seu conteúdo.

      >[!TIP]
      >
      >Essa opção é exibida somente quando você seleciona o tipo de mensagem **[!UICONTROL Tela cheia]**.

   * **[!UICONTROL Personalizado]**

      Carregue seu conteúdo HTML personalizado (somente tela cheia). Você deve fornecer um link click-through e um link de cancelamento.

      1. Clique em **[!UICONTROL Procurar]** e baixe um arquivo HTML ou arraste um documento HTML até a janela.
      1. Clique em **[!UICONTROL Baixar exemplo]** para exibir o modelo de conteúdo HTML personalizado.

      >[!TIP]
      >
      >Essa opção é exibida somente quando você seleciona o tipo de mensagem **[!FTela cheia]**.



1. Preencha os campos na seção **[!UICONTROL Exibir]**:

   * **[!UICONTROL Tema]**

   Selecione um tema para a mensagem.

   * **[!UICONTROL Layout]**

      Selecione o layout do aplicativo na tela do dispositivo.

   * **[!UICONTROL URL da imagem]**

      O URL de uma imagem. Em caso de problemas de dimensionamento ao usar o modelo de tela cheia, consulte *Minha imagem não se encaixa perfeitamente no espaço fornecido pelo modelo* em [Solução de problemas de mensagens no aplicativo](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL Imagem embutida]**

      Caminho para uma imagem no conjunto de códigos do aplicativo. Essa opção é usada quando não há imagem. ou a imagem não está disponível. A imagem talvez não esteja disponível se, por exemplo, o dispositivo estiver offline. Em caso de problemas de dimensionamento ao usar o modelo de tela cheia, consulte *Minha imagem não se encaixa perfeitamente no espaço fornecido pelo modelo* em [Solução de problemas de mensagens no aplicativo](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. Preencha os campos na seção **[!UICONTROL Texto]**:

   * **[!UICONTROL Header]**

      Digite o texto para o cabeçalho da mensagem.

   * **[!UICONTROL Conteúdo]**

      Digite o texto para o conteúdo da mensagem.

1. Preencha os campos na seção **[!UICONTROL Botões]**:

   * **[!UICONTROL Botão de Click-Through]**

      Rótulo para o botão de **[!UICONTROL Click-through]**. Tocar nesse botão contará como um click-through bem-sucedido. O usuário é redirecionado para o destino.

   * **[!UICONTROL Destino]**

      Selecione um destino específico (como um link da Web, deep link ou link híbrido) para enviar os usuários quando eles clicarem na mensagem. O URL de redirecionamento para um click-through bem-sucedido.

      Este URL pode conter as seguintes informações:

      * `{userId}`, que é substituído pelo identificador do usuário ou está em branco quando o identificador não é definido.
      * `{trackingId}`, que é substituído pelo parâmetro aid (correlação com o cookie *s_vi*).
      * `{messageId}`, que é substituído pela ID exclusiva para a mensagem no aplicativo.
      * `{lifetimeValue}`, que é substituído pelo valor da duração ou por zero caso não exista tal valor.

      Veja um exemplo do rastreamento da ID do usuário: `https://www.mysite.com?uid={userId}`.

      Se o URL de click-through usar `https://` ou `https://`, o URL é aberto no navegador do dispositivo fora do aplicativo. Caso contrário, cada plataforma suportará esquemas que permitem abrir ou consultar o aplicativo se ele tiver sido desenvolvido para oferecer suporte ao esquema personalizado.

      >[!TIP]
      >
      >Se você usar os tipos de destino **[!UICONTROL Link da Web]** ou **[!UICONTROL Link personalizado]**, o tipo de destino não é rastreado. Somente os **[!UICONTROL deep links]** são rastreados. Para obter mais informações, consulte [Destinos](/help/using/acquisition-main/c-create-destinations.md).


1. (Opcional) Visualize o layout de sua mensagem clicando nos ícones a seguir:

   * **[!UICONTROL Resumo]** oculta o painel de visualização.

      Clique em ![visualização](assets/icon_preview.png) para exibir novamente o painel de visualização.

   * **[!UICONTROL Alterar a orientação]**

      Para alterar a orientação da visualização do modo retrato para paisagem, clique em ![orientação](assets/icon_orientation.png). Nos relógios, a orientação muda o mostrador do relógio de redondo para quadrado.

   * **[!UICONTROL Visualizar no relógio de um usuário]**

      Para visualizar sua mensagem como ela aparecerá no relógio do usuário, clique em ![watch icon](assets/icon_watch.png).

   * **[!UICONTROL Visualizar no celular de um usuário]**

      Para visualizar sua mensagem como ela aparecerá no celular de um usuário, clique em ![phone icon](assets/icon_phone.png).

   * **[!UICONTROL Visualizar no tablet de um usuário]**

      Para visualizar sua mensagem no tablet de um usuário, clique em ![tablet icont](assets/icon_tablet.png).

      Na parte inferior do painel de visualização, você pode ver uma descrição do público-alvo selecionado na etapa anterior. Na parte inferior do painel de visualização também é possível exibir uma descrição do público-alvo selecionado na etapa anterior.

1. Configurar as [Opções de programação](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md).
