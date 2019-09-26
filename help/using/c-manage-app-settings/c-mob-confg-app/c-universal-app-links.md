---
description: Links universais (iOS) e Links de aplicativo (Android) permitem conectar-se a deep links nos aplicativos iOS ou Android.
keywords: mobile
seo-description: Links universais (iOS) e Links de aplicativo (Android) permitem conectar-se a deep links nos aplicativos iOS ou Android.
seo-title: Links universais da Apple e links de aplicativos Android
solution: Marketing Cloud,Analytics
title: Links universais da Apple e links de aplicativos Android
topic: Métricas
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Links universais da Apple e links de aplicativos Android{#universal-links-and-app-links}

Links universais (iOS) e Links de aplicativo (Android) permitem conectar-se a deep links nos aplicativos iOS ou Android.

>[!IMPORTANT]
>
>A partir do iOS 9.2, não há suporte para deep linking. Você deve usar o Apple Universal Links para criar deep links para seu aplicativo ou site.

## Links universais {#section_F8147944679A42E59CF4FD8814E5EF12}

Links universais permitem conectar-se a deep links no aplicativo iOS e são compatíveis com o iOS 9.2 ou posterior. Quando um Link universal é acessado, o iOS redireciona o link diretamente para o link direto no aplicativo. Se seu aplicativo não estiver instalado, ele abre um URL para seu site em um navegador. Para obter mais informações sobre Links universais, consulte [Suporte a links](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)universais.

## Links de aplicativo

Os Links de aplicativo permitem conectar-se a deep links no aplicativo Android e são compatíveis com o Android 6.0 ou posterior. Quando um link de aplicativo é acessado, o Android redireciona o link diretamente para o deep link no aplicativo. If your app is not installed, it opens a URL for your website in a browser instead. For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## Criar um link de marketing usando um link universal ou de aplicativo {#section_609ADEFFB9B441C4A8C45E936D0DC859}

You can create a Marketing Link that uses a Universal or App Link.

### Configure a Universal Link

1. Para configurar links universais no aplicativo iOS, vá para [Manuseio de links universais na Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. In Adobe Mobile Services, set up the site-association documents:

   a. Na página inicial do Mobile Services, selecione o aplicativo para o qual deseja configurar Links universais.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Ensure the iOS app that handles the Universal Links is added to the **[!UICONTROL Add App Store Apps]** section.

   >[!TIP]
   >
   >If the **[!UICONTROL Add App Store Apps]** section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. Na seção Opções **[!UICONTROL de links]** universais e links de aplicativos, selecione um aplicativo iOS e digite a ID do aplicativo.

   f. Click Save.****

   You must provide at least one iOS app selection and one App ID, or you will receive an error.

   >[!IMPORTANT]
   >
   >Você pode atualizar os documentos clicando em Atualizar na seção opções de Links Universais e Links de Aplicativo. However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Usar um link universal

1. In Adobe Mobile Services, create a Marketing Link that uses Universal Links:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Click Create New.****

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. If you configured the site-association documents in the Setting up site-association documents in Adobe Mobile Services section above, this option is selected by default.**

   If you did not configure the documents, the Use Universal Links or App Links option is disabled and Use Interstitials is selected by default.********

   e. If the Use Universal Links or App Links option is selected, the Custom Path field is displayed.********

   Isso permite que os usuários definam o caminho do URL após o domínio com qualquer parâmetro de consulta. Por exemplo, se você digitar , your full Marketing Link URL becomes .`my/universal/link?os=9.2``https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`

   f. Click the Decisions tab and configure your decision tree.****

   h. Se o aplicativo iOS estiver instalado, o aplicativo lidará com o deep link com sua lógica. O destino final serve apenas como fallback quando o aplicativo não está instalado. Como o aplicativo não está instalado, o destino final só pode ser um link da Web ou uma loja de aplicativos.

   i.Clique em **[!UICONTROL Salvar]**.

>[!TIP]
>
>Quando um Link de marketing é salvo, as Opções de links de marketing não podem ser alteradas. Isso ocorre porque você não deseja alterar o comportamento dos Links de marketing que já podem ter sido distribuídos.


### Configurar um link de aplicativo

1. Para configurar links de aplicativos no aplicativo Android, vá para [Adicionar links](https://developer.android.com/studio/write/app-link-indexing)de aplicativos Android.

1. No Adobe Mobile Services, configure os documentos de associação ao site:

   a. In the Mobile Services home page, select the app for which you want to set up App Links.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Certifique-se de que o aplicativo Android que lida com links universais ou links de aplicativos seja adicionado à seção **[!UICONTROL Adicionar aplicativos]** da App Store.

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. Role até a seção Opções **[!UICONTROL de links]** universais e links de aplicativos.

   e. Clique na guia Links de **[!UICONTROL aplicativo (Android)]** .

   f. Selecione um aplicativo Android e digite uma impressão digital SHA-256 certificada.

   g.Clique em **[!UICONTROL Salvar]**.

   Você deve fornecer pelo menos uma seleção de aplicativo Android e um certificado SHA-256, caso contrário aparecerá um erro.

   >[!IMPORTANT]
   >
   >Você pode atualizar os documentos clicando em **[!UICONTROL Atualizar]** na seção **opções de Links Universais e Links de Aplicativo[!UICONTROL .]** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Usar um link de aplicativo

1. No Adobe Mobile Services, crie um Marketing Link que use Links de aplicativo:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Clique em **[!UICONTROL Criar novo]**.

   c. Na seção Opções **[!UICONTROL de link de]** marketing, selecione **[!UICONTROL Usar links universais ou links]** de aplicativos.

   d. If you configured the site-association documents from step 2, this option is selected by default.

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. Se **[!UICONTROL Usar links universais ou links]** de aplicativos estiver selecionado, o campo Caminho **** personalizado será exibido.

   Isso permite que os usuários definam o caminho do URL após o domínio com qualquer parâmetro de consulta. Por exemplo, se você digitar `my/app/link?os=6.0`, seu URL completo do Marketing Link se torna `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Clique na guia **[!UICONTROL Decisões]** e configure sua árvore decisória.

   g. Se o aplicativo Android estiver instalado, o aplicativo lidará com o deep link com sua lógica.

   O destino final serve apenas como o caso de fallback para quando o aplicativo não está instalado. Como o aplicativo não está instalado, o destino final só pode ser um link da Web ou uma loja de aplicativos.

   h.Clique em **[!UICONTROL Salvar]**.

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. Isso ocorre porque você não deseja alterar o comportamento dos Links de marketing que já podem ter sido distribuídos.

## Uso de links de marketing

Agora você pode usar esses Links de marketing em mensagens e outras áreas do aplicativo.

>[!IMPORTANT]
>
>Você não verá as contagens de rastreamento de cliques com Links Universais ou Links de Aplicativo, e também não poderá usar intersticiais.

