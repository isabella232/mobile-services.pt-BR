---
description: Você pode configurar seu aplicativo para usar o Apple Push Notification Service (APNS) ou o Firebase Cloud Messaging (FCM).
keywords: mobile
seo-description: Você pode configurar seu aplicativo para usar o Apple Push Notification Service (APNS) ou o Firebase Cloud Messaging (FCM).
seo-title: Configurar o aplicativo para usar APNS ou FCM
solution: Marketing Cloud,Analytics
title: Configure App to use APNS or FCM
topic: Métricas
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# Configure your app to use APNS or FCM{#configure-app-to-use-apns-or-fcm}

Você pode configurar seu aplicativo para usar o Apple Push Notification Service (APNS) ou o Firebase Cloud Messaging (FCM).

## Aplicativos Android {#section_41D304102CDF4586911EC1413AD35A10}

### Se o FCM não estiver ativado no aplicativo

To configure your Android app to use FCM in this scenario:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Click **[!UICONTROL Get Started]** and select **[!UICONTROL Add Project]**.

1. Enter a project name and if opting in to Google Analytics for Firebase data, click the checkbox accepting the controller-controller terms.

1. Click Create project and wait for the project to be created.****

1. Click on the created project and the Project Overview page for the created project should be shown. **** Click the button with the Android icon to add an Android app to the project.

1. Digite o nome do pacote do aplicativo, o apelido do aplicativo e o certificado de assinatura, se necessário.

1. Siga as etapas adicionais sugeridas pelo assistente de configuração. Após verificar a configuração do Firebase testando a comunicação com os servidores Firebase, volte à página Visão geral **[!UICONTROL do]** projeto.

1. Clique no ícone de engrenagem à direita do botão Visão geral **[!UICONTROL do]** projeto e clique em Configurações **** do projeto.

1. Clique na guia Mensagens **[!UICONTROL em]** nuvem.

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   Por exemplo:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### Se o FCM estiver ativado no aplicativo

Para configurar seu aplicativo Android para usar o FCM neste cenário:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Clique em **[!UICONTROL Introdução]**. Isso abrirá a página de índice do projeto. Localize o projeto ativado pelo Firebase vinculado ao aplicativo Android e clique no cartão do projeto.

1. A Visão geral **[!UICONTROL do]** projeto deve ser carregada. Clique no ícone de engrenagem à direita do botão Visão geral **[!UICONTROL do]** projeto e clique em Configurações **** do projeto.

1. Clique na guia Mensagens **[!UICONTROL em]** nuvem.

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
1. If you have an App ID set up for push, go to Step 11.
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

   O botão em que você clica depende de você estar criando um certificado para Desenvolvimento ou Produção.
1. Siga as etapas sobre como criar seu CSR no site da Apple, fazer upload do CSR e gerar seu certificado.
1. Role para baixo até a seção **[!UICONTROL Notificações por push]** e baixe o certificado SSL que você acabou de criar.
1. Clique duas vezes no certificado baixado para adicioná-lo ao seu conjunto de chaves.

### Certificado SSL e chaves privadas

To get your SSL certificate and private key (APNS):

1. Abra **[!UICONTROL Acesso ao chaveiro]**.
1. Clique em **[!UICONTROL Meus certificados]** e localize o **[!UICONTROL Certificado de serviços por do iOS]** apropriado para seu aplicativo e ambiente.

   Você pode identificar o certificado correto ao corresponder a ID do pacote e se é de Desenvolvimento ou Produção.

1. Amplie o certificado e confira se ele contém uma chave privada.
1. Clique com o botão direito do mouse na chave privada e selecione **[!UICONTROL Exportar "*`<name of key>`*]**.
1. Digite as informações necessárias na caixa de diálogo e salve o novo `.p12` arquivo.

   Não é necessário digitar uma senha.

1. In the **[!UICONTROL Private Key]**, type the `.p12` file.

