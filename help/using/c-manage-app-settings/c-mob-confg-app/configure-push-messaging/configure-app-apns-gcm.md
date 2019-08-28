---
description: Você pode configurar seu aplicativo para usar o Apple Push Notification Service (APNS) ou o Firebase Cloud Messaging (FCM).
keywords: mobile
seo-description: Você pode configurar seu aplicativo para usar o Apple Push Notification Service (APNS) ou o Firebase Cloud Messaging (FCM).
seo-title: Configurar aplicativo para usar o APNS ou FCM
solution: Marketing Cloud, Analytics
title: Configurar aplicativo para usar o APNS ou FCM
topic: Métricas
uuid: fa 411 f 2 a-ba 47-4499-bbe 5-1 aedef 6 b 49
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# Configurar seu aplicativo para usar o APNS ou FCM{#configure-app-to-use-apns-or-fcm}

Você pode configurar seu aplicativo para usar o Apple Push Notification Service (APNS) ou o Firebase Cloud Messaging (FCM).

## Aplicativos Android {#section_41D304102CDF4586911EC1413AD35A10}

### Se o FCM não estiver ativado no aplicativo

Para configurar seu aplicativo Android para usar FCM neste cenário:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Clique **[!UICONTROL em Introdução]** e selecione **[!UICONTROL Adicionar projeto]**.

1. Digite um nome de projeto e se estiver inscrito para os dados do Google Analytics para Firebase, clique na caixa de seleção que aceita os termos do controlador de controlador.

1. Clique **[!UICONTROL em Criar projeto]** e aguarde a criação do projeto.

1. Clique no projeto criado e a **[!UICONTROL página Visão geral]** do projeto para o projeto criado deve ser exibida. Clique no botão com o ícone Android para adicionar um aplicativo Android ao projeto.

1. Insira o nome do pacote do aplicativo, o apelido do aplicativo e o certificado de assinatura, se necessário.

1. Siga as etapas adicionais sugeridas pelo assistente de configuração. Depois de verificar a configuração do Firebase testando comunicação com os servidores Firebase, retorne à página **[!UICONTROL Visão geral]** do projeto.

1. Clique no ícone de engrenagem à direita do **[!UICONTROL botão Visão geral]** do projeto e clique **[!UICONTROL em Configurações de projeto]**.

1. Clique na **[!UICONTROL guia Nuvem Messaging]** .

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   Por exemplo:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### Se o FCM estiver ativado no aplicativo

Para configurar seu aplicativo Android para usar FCM neste cenário:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Clique **[!UICONTROL em Introdução]**. Isso abrirá a página de índice do projeto. Encontre o projeto ativado do Firebase, vinculado ao seu aplicativo Android e clique no cartão do projeto.

1. A Visão geral **[!UICONTROL do projeto]** para o projeto deve ser carregada. Clique no ícone de engrenagem à direita do **[!UICONTROL botão Visão geral]** do projeto e clique **[!UICONTROL em Configurações de projeto]**.

1. Clique na **[!UICONTROL guia Nuvem Messaging]** .

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   Por exemplo:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS apps {#section_2031DAB485FC4D2B9027E42AD90B294D}

Para configurar o aplicativo iOS para usar o APNS:

1. Acesse [https://developer.apple.com/account](https://developer.apple.com/account) e faça logon com sua [conta de desenvolvedor da Apple](https://developer.apple.com/account).
1. Em **[!UICONTROL Aplicativos iOS]**, selecione **[!UICONTROL Identificadores]**.
1. Se você tiver uma ID de aplicativo configurada para push, vá para a Etapa 11.
1. Press the **[!UICONTROL +]** button to create a new App ID.
1. Digite uma descrição da ID do aplicativo.
1. Digite um sufixo da ID do aplicativo.

   >[!IMPORTANT]
   >
   >To support push, you must use an Explicit App ID that does **not** use a wild card (for example, `- com.tester.pushSample`).

1. Em **[!UICONTROL Serviços do aplicativo]**, marque a caixa de seleção **[!UICONTROL Notificações por push]**.
1. Clique em **[!UICONTROL Continuar]**.
1. Clique em **[!UICONTROL Enviar]**.
1. Clique em **[!UICONTROL Concluído]**.
1. Selecione a ID do aplicativo configurada para usar mensagens de push na lista e clique em **[!UICONTROL Editar]**.
1. Se você já tiver criado um certificado push, pule para a Etapa 15.
1. Role para baixo até **[!UICONTROL Notificações por push]** e clique no botão **[!UICONTROL Criar certificado…]** correto.

   O botão clicado depende se você está criando um certificado para Desenvolvimento ou Produção.
1. Siga as etapas sobre como criar seu CSR no site da Apple, fazer upload do CSR e gerar seu certificado.
1. Role para baixo até a seção **[!UICONTROL Notificações por push]** e baixe o certificado SSL que você acabou de criar.
1. Clique duas vezes no certificado baixado para adicioná-lo ao seu conjunto de chaves.

### Certificado SSL e chaves privadas

Para obter o certificado SSL e a chave privada (APNS):

1. Abra **[!UICONTROL Acesso ao chaveiro]**.
1. Clique em **[!UICONTROL Meus certificados]** e localize o **[!UICONTROL Certificado de serviços por do iOS]** apropriado para seu aplicativo e ambiente.

   Você pode identificar o certificado correto ao corresponder a ID do pacote e se é de Desenvolvimento ou Produção.

1. Amplie o certificado e confira se ele contém uma chave privada.
1. Clique com o botão direito do mouse na chave privada e selecione **[!UICONTROL Exportar "*`<name of key>`*]**.
1. Digite as informações necessárias na caixa de diálogo e salve o novo `.p12` arquivo.

   Não é necessário digitar uma senha.

1. In the **[!UICONTROL Private Key]**, type the `.p12` file.

