---
description: É possível configurar seu aplicativo para usar o Serviço de notificação por push da Apple (APNS) ou o Firebase Cloud Messaging (FCM).
keywords: dispositivos móveis
seo-description: É possível configurar seu aplicativo para usar o Serviço de notificação por push da Apple (APNS) ou o Firebase Cloud Messaging (FCM).
seo-title: Configurar o aplicativo para uso do APNS ou do FCM
solution: Experience Cloud,Analytics
title: Configurar o aplicativo para uso do APNS ou do FCM
topic-fix: Metrics
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
exl-id: 9064e1f3-f176-4699-b1e6-90f29e1af0d3
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 100%

---

# Configurar o aplicativo para uso do APNS ou do FCM {#configure-app-to-use-apns-or-fcm}

É possível configurar seu aplicativo para usar o Serviço de notificação por push da Apple (APNS) ou o Firebase Cloud Messaging (FCM).

## Aplicativos Android {#section_41D304102CDF4586911EC1413AD35A10}

### Se o FCM não estiver ativado no aplicativo

Nesse caso, para configurar seu aplicativo Android para usar o FCM, siga os passos seguintes:

1. Acesse [https://firebase.google.com/](https://firebase.google.com/) e faça logon com suas credenciais de desenvolvedor do Google.

1. Clique em **[!UICONTROL Introdução]** e selecione **[!UICONTROL Adicionar projeto]**.

1. Insira um nome de projeto e, caso opte pelo Google Analytics para dados de Firebase, clique na caixa de seleção para aceitar os termos de controlador-controlador.

1. Clique em **[!UICONTROL Criar projeto]** e aguarde a criação do projeto.

1. Clique no projeto criado e na página **[!UICONTROL Visão geral do projeto]** para exibir o projeto criado. Clique no botão com o ícone do Android para adicionar um aplicativo Android ao projeto.

1. Insira o nome do pacote do aplicativo, o apelido do aplicativo e o certificado de autenticação, caso necessário.

1. Siga as etapas adicionais sugeridas pelo assistente de configuração. Uma vez confirmada a configuração do Firebase com o teste de comunicação com os servidores do Firebase, volte para a página **[!UICONTROL Visão geral do projeto]**.

1. Clique no ícone de engrenagem à direita do botão **[!UICONTROL Visão geral do projeto]** e clique em **[!UICONTROL Configurações do projeto]**.

1. Clique na guia **[!UICONTROL Cloud Messaging]**.

1. Copie a **[!UICONTROL chave do servidor herdado]** e a **[!UICONTROL ID do remetente]** para uso posterior.

   Por exemplo:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### Se o FCM estiver ativado no aplicativo

Nesse caso, para configurar seu aplicativo Android para usar o FCM, siga os passos seguintes:

1. Acesse [https://firebase.google.com/](https://firebase.google.com/) e faça logon com suas credenciais de desenvolvedor do Google.

1. Clique em **[!UICONTROL Introdução]**. Isso abrirá a página de índice do projeto. Localize o projeto ativado no Firebase, vinculado ao aplicativo Android, e clique no cartão do projeto.

1. A **[!UICONTROL Visão geral do projeto]** para o projeto deve ser carregada. Clique no ícone de engrenagem à direita do botão **[!UICONTROL Visão geral do projeto]** e clique em **[!UICONTROL Configurações do projeto]**.

1. Clique na guia **[!UICONTROL Cloud Messaging]**.

1. Copie a **[!UICONTROL chave do servidor herdado]** e a **[!UICONTROL ID do remetente]** para uso posterior.

   Por exemplo:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## Aplicativos iOS {#section_2031DAB485FC4D2B9027E42AD90B294D}

Para configurar o aplicativo iOS para usar o APNS:

1. Acesse [https://developer.apple.com/account](https://developer.apple.com/account) e faça logon em sua [conta de desenvolvedor da Apple](https://developer.apple.com/account).
1. Em **[!UICONTROL Aplicativos iOS]**, selecione **[!UICONTROL Identificadores]**.
1. Se você tiver uma ID do aplicativo configurada para push, vá para a Etapa 11.
1. Pressione o botão **[!UICONTROL +]** para criar uma nova ID do aplicativo.
1. Digite uma descrição da ID do aplicativo.
1. Digite um sufixo da ID do aplicativo.

   >[!IMPORTANT]
   >
   >Para ser compatível com push, você deve usar uma ID do aplicativo explícita que **não** use curinga (por exemplo, `- com.tester.pushSample`).

1. Em **[!UICONTROL Serviços do aplicativo]**, marque a caixa de seleção **[!UICONTROL Notificações por push]**.
1. Clique em **[!UICONTROL Continuar]**.
1. Clique em **[!UICONTROL Enviar]**.
1. Clique em **[!UICONTROL Concluído]**.
1. Selecione a ID do aplicativo configurada para usar mensagens de push na lista e clique em **[!UICONTROL Editar]**.
1. Se você já tiver criado um certificado push, pule para a Etapa 15.
1. Role para baixo até **[!UICONTROL Notificações por push]** e clique no botão **[!UICONTROL Criar certificado…]** correto.

   O botão é diferente para as hipóteses de criação de um certificado de Desenvolvimento ou Produção.
1. Sigas as etapas para criar seu CSR no site da Apple, fazer upload do CSR e gerar seu certificado.
1. Role para baixo até a seção **[!UICONTROL Notificações por push]** e baixe o certificado SSL que você acabou de criar.
1. Clique duas vezes no certificado baixado para adicioná-lo ao seu chaveiro.

### Certificado SSL e chaves privadas

Para obter o certificado SSL e a chave privada (APNS):

1. Abra **[!UICONTROL Acesso ao chaveiro]**.
1. Clique em **[!UICONTROL Meus certificados]** e localize o **[!UICONTROL Certificado de serviços por do iOS]** apropriado para seu aplicativo e ambiente.

   É possível identificar o certificado correto ao corresponder à ID do pacote e determinando se é Desenvolvimento ou Produção.

1. Expanda o certificado e verifique se ele contém uma chave privada.
1. Clique com o botão direito do mouse na chave privada e selecione **[!UICONTROL Exportar &quot;*`<name of key>`*]**.
1. Digite as informações necessárias na caixa de diálogo e salve o novo arquivo `.p12`.

   Não é necessário digitar uma senha.

1. Na **[!UICONTROL Chave privada]**, digite o arquivo `.p12`.
