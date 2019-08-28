---
description: Links universais (iOS) e Links de aplicativo (Android) permitem a conexão com deep links nos aplicativos iOS ou Android.
keywords: mobile
seo-description: Links universais (iOS) e Links de aplicativo (Android) permitem a conexão com deep links nos aplicativos iOS ou Android.
seo-title: Links de aplicativos do Apple Universal Links e do Android
solution: Marketing Cloud, Analytics
title: Links de aplicativos do Apple Universal Links e do Android
topic: Métricas
uuid: 8 d 6441 dc -4307-4454-95 ea-d 77 ec 796 f 918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Links de aplicativos do Apple Universal Links e do Android{#universal-links-and-app-links}

Links universais (iOS) e Links de aplicativo (Android) permitem a conexão com deep links nos aplicativos iOS ou Android.

>[!IMPORTANT]
>
>A partir do iOS 9.2, o deep linking não é suportado. Você deve usar Links universais da Apple para deep links no seu aplicativo ou site da Web.

## Links universais {#section_F8147944679A42E59CF4FD8814E5EF12}

Links universais permitem se conectar aos deep links no aplicativo iOS e têm suporte no iOS 9.2 ou posterior. Quando um Link universal é acessado, o iOS redireciona o link diretamente para o deep link no aplicativo. Se o aplicativo não estiver instalado, ele abre um URL para seu site em um navegador. Para obter mais informações sobre Links universais, consulte [Suporte aos Links Universais](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html).

## Links de aplicativo

Links de aplicativo permitem se conectar aos deep links no aplicativo Android e são compatíveis com o Android 6.0 ou posterior. Quando um Link de aplicativo é acessado, o Android redireciona o link diretamente para o deep link no aplicativo. Se o aplicativo não estiver instalado, ele abre um URL para seu site em um navegador. For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## Criar um link de marketing usando um link universal ou de aplicativo {#section_609ADEFFB9B441C4A8C45E936D0DC859}

Você pode criar um Link de marketing que usa um Link universal ou de aplicativo.

### Configurar um link universal

1. Para configurar Links universais no aplicativo iOS, vá para [Gerenciar links universais na Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. Nos Adobe Mobile Services, configure os documentos de associação do site:

   a. Na página inicial do Mobile Services, selecione o aplicativo para o qual deseja configurar Links Universais.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Certifique-se de que o aplicativo iOS que controla os Links universais seja adicionado à seção **[!UICONTROL Adicionar aplicativos]** da App Store.

   >[!TIP]
   >
   >Se a seção **[!UICONTROL Adicionar aplicativos]** da App Store não for exibida, clique no link **[!UICONTROL Adicionar aplicativo]** da App Store.

   d. Na seção Opções **[!UICONTROL de Links universais e Links de aplicativo,]** selecione um aplicativo iOS e digite a ID do aplicativo.

   f. Clique **[!UICONTROL em Salvar]**.

   Você deve fornecer pelo menos uma seleção de aplicativo iOS e uma ID de aplicativo, ou receberá um erro.

   >[!IMPORTANT]
   >
   >Você pode atualizar os documentos clicando em Atualizar na seção opções de Links Universais e Links de Aplicativo. However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Usar um link universal

1. No Adobe Mobile Services, crie um Link de marketing que use Links universais:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Clique **[!UICONTROL em Criar novo]**.

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. Se você configurar os documentos de associação do site na *seção Configuração de documentos de associação do site na seção Adobe* Mobile Services acima, esta opção estará selecionada por padrão.

   Se você não tiver configurado os documentos, a opção **[!UICONTROL Usar links universais ou links]** de aplicativo estará desativada e **[!UICONTROL Usar intersticiais]** estará selecionado por padrão.

   e. Se a opção **[!UICONTROL Usar links universais ou links]** de aplicativo estiver selecionada, o **[!UICONTROL campo Caminho]** personalizado será exibido.

   Isso permite que os usuários definam o caminho do URL após o domínio com qualquer parâmetro de consulta. Por exemplo, se você digitar `my/universal/link?os=9.2`, toda a URL do link de marketing será disponibilizada `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`.

   f. Clique na **[!UICONTROL guia Decisões]** e configure a árvore de decisão.

   h. Se o aplicativo iOS estiver instalado, o aplicativo lida com o deep link com sua lógica. O destino final serve apenas como o fallback quando o aplicativo não está instalado. Como o aplicativo não está instalado, o destino final pode ser apenas um link da Web ou uma app store.

   i. Clique **[!UICONTROL em Salvar]**.

>[!TIP]
>
>Depois que um Marketing Link é salvo, as Opções de links de marketing não podem ser alteradas. Isso ocorre porque você não deseja alterar o comportamento dos Links de publicidade que já podem ter sido distribuídos.


### Configurar um link de aplicativo

1. Para configurar Links de aplicativo no aplicativo Android, vá para [Adicionar links](https://developer.android.com/studio/write/app-link-indexing)de aplicativos Android.

1. Nos Adobe Mobile Services, configure os documentos de associação do site:

   a. Na página inicial do Mobile Services, selecione o aplicativo para o qual deseja configurar Links de aplicativo.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Verifique se o aplicativo Android que controla Links universais ou Links de aplicativo foi adicionado à seção **[!UICONTROL Adicionar aplicativos]** da App Store.

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. Role até a **[!UICONTROL seção Opções]** de Links universais e Links de aplicativo.

   e. Clique na **[!UICONTROL guia Links de aplicativo (Android)]** .

   f. Selecione um aplicativo Android e digite uma impressão digital SHA -256.

   g. Clique **[!UICONTROL em Salvar]**.

   Você deve fornecer pelo menos uma seleção de aplicativo Android e um certificado SHA -256 ou receberá um erro.

   >[!IMPORTANT]
   >
   >Você pode atualizar os documentos clicando em **[!UICONTROL Atualizar]** na seção **opções de Links Universais e Links de Aplicativo[!UICONTROL .]** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Usar um link de aplicativo

1. No Adobe Mobile Services, crie um Link de marketing que use Links de aplicativo:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Clique **[!UICONTROL em Criar novo]**.

   c. Na seção **[!UICONTROL Opções]** do link de marketing, selecione **[!UICONTROL Usar links universais ou links de aplicativo]**.

   d. Se você configurar os documentos de associação do site da etapa 2, essa opção estará selecionada por padrão.

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. Se **[!UICONTROL Usar Links universais ou Links de aplicativo]** estiver selecionado, **[!UICONTROL o campo Caminho]** personalizado será exibido.

   Isso permite que os usuários definam o caminho do URL após o domínio com qualquer parâmetro de consulta. Por exemplo, se você digitar `my/app/link?os=6.0`, toda a URL do link de marketing será disponibilizada `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Clique na **[!UICONTROL guia Decisões]** e configure a árvore de decisão.

   g. Se o aplicativo Android estiver instalado, o aplicativo lida com o deep link com sua lógica.

   O destino final serve apenas como o caso de fallback para quando o aplicativo não está instalado. Como o aplicativo não está instalado, o destino final pode ser apenas um link da Web ou uma app store.

   h. Clique **[!UICONTROL em Salvar]**.

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. Isso ocorre porque você não deseja alterar o comportamento dos Links de publicidade que já podem ter sido distribuídos.

## Uso de links de marketing

Agora você pode usar esses Links de publicidade em mensagens e outras áreas no aplicativo.

>[!IMPORTANT]
>
>Você não verá contagens de rastreamento de cliques com Links universais ou Links de aplicativo, e também não pode usar intersticiais.

