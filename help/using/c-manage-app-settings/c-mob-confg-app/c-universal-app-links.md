---
description: Com os Links universais (iOS) e os Links de aplicativo (Android), é possível se conectar a links profundos nos aplicativos iOS ou Android.
keywords: mobile
seo-description: Com os Links universais (iOS) e os Links de aplicativo (Android), é possível se conectar a links profundos nos aplicativos iOS ou Android.
seo-title: Links universais da Apple e links de aplicativos Android
solution: Experience Cloud,Analytics
title: Links universais da Apple e links de aplicativos Android
topic: Metrics
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 100%

---


# Links universais da Apple e links de aplicativos Android {#universal-links-and-app-links}

Com os Links universais (iOS) e os Links de aplicativo (Android), é possível se conectar a links profundos nos aplicativos iOS ou Android.

>[!IMPORTANT]
>
>A partir do iOS 9.2, não há suporte para links profundos. Você deve usar os Links universais da Apple para criar links profundos para seu aplicativo ou site.

## Links universais {#section_F8147944679A42E59CF4FD8814E5EF12}

Com os Links universais, é possível se conectar a links profundos no aplicativo iOS. Eles também são compatíveis com o iOS 9.2 ou versão posterior. Quando um Link universal é acessado, o iOS redireciona o link diretamente para o link profundo no aplicativo. Se seu aplicativo não estiver instalado, ele abre um URL para o seu site em um navegador. Para obter mais informações sobre Links universais, consulte [Links universais compatíveis](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html).

## Links de aplicativo

Com os Links de aplicativo, é possível conectar-se a links profundos no aplicativo Android. Eles também são compatíveis com o Android 6.0 ou versão posterior. Quando um Link de aplicativo é acessado, o Android redireciona o link diretamente para o link profundo no aplicativo. Se seu aplicativo não estiver instalado, ele abre um URL para o seu site em um navegador. Para obter mais informações sobre Links de aplicativo, consulte [Trabalho com Links de aplicativo Android](https://developer.android.com/training/app-links/index.html).

## Criar um Link de marketing usando um Link universal ou de aplicativo {#section_609ADEFFB9B441C4A8C45E936D0DC859}

Você pode criar um Link de marketing que use um Link universal ou de aplicativo.

### Configurar um Link universal

1. Para configurar links universais no aplicativo iOS, vá para [Trabalho com Links universais em aparelhos Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. No Adobe Mobile Services, configure os documentos de associação ao site:

   a. Na página inicial do Mobile Services, selecione o aplicativo para o qual deseja configurar Links universais.

   b. Clique em **[!UICONTROL Gerenciar configurações do aplicativo]**.

   c. Verifique se o aplicativo iOS que manipula os Links universais foi adicionado à seção **[!UICONTROL Adicionar aplicativos da loja de aplicativos]**.

   >[!TIP]
   >
   >Se a seção **[!UICONTROL Adicionar aplicativos da loja de aplicativos]** não for exibida, clique no link **[!UICONTROL Adicionar aplicativo da loja de aplicativos]**.

   d. Na seção **[!UICONTROL Opções de links universais e links de aplicativos]**, selecione um aplicativo iOS e digite a ID do aplicativo.

   f. Clique em **[!UICONTROL Salvar]**.

   Você deve fornecer pelo menos uma seleção de aplicativo iOS e uma ID de aplicativo, ou receberá um erro.

   >[!IMPORTANT]
   >
   >Você pode atualizar os documentos clicando em Atualizar na seção opções de Links Universais e Links de Aplicativo. Porém, quando você clica em **[!UICONTROL Atualizar]**, um aviso notifica que todos os Links universais ou de aplicativos que você criou no passado serão afetados.

### Usar um Link universal

1. No Adobe Mobile Services, crie um Link de marketing que use Links universais:

   a. Selecione o aplicativo na página inicial do Mobile Services, clique em **[!UICONTROL Aquisição]** > **[!UICONTROL Construtor do Link de marketing]**.

   b. Clique em **[!UICONTROL Criar novo]**.

   c. Em **[!UICONTROL Opções do Link de marketing]**, selecione **[!UICONTROL Usar links universais ou links de aplicativos]**.

   d. Se você tiver configurado os documentos de associação ao site na seção *Configuração de documentos de associação ao site no Adobe Mobile Services* acima, essa opção será selecionada por padrão.

   Se você não tiver configurado os documentos, a opção **[!UICONTROL Usar Links universais ou Links de aplicativos]** estará desativada e **[!UICONTROL Usar intersticiais]** será selecionado por padrão.

   e. Se a opção **[!UICONTROL Usar links universais ou links de aplicativos]** estiver selecionada, o campo **[!UICONTROL Caminho personalizado]** será exibido.

   Isso permite que os usuários definam o caminho do URL após o domínio com qualquer parâmetro de consulta. Por exemplo, se você digitar   `my/universal/link?os=9.2`, seu URL completo do Link de marketing se torna `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`.

   f. Clique na guia **[!UICONTROL Decisões]** e configure sua árvore decisória.

   h. Se o aplicativo iOS estiver instalado, o aplicativo processará o link profundo de acordo com sua lógica. O destino final serve apenas como fallback quando o aplicativo não está instalado. Como o aplicativo não está instalado, o destino final só pode ser um link da Web ou uma loja de aplicativos.

   i. Clique em **[!UICONTROL Salvar]**.

>[!TIP]
>
>Quando um Link de marketing é salvo, as Opções dos Links de marketing não podem ser alteradas. Isso ocorre porque você não é desejável alterar o comportamento dos Links de marketing que já foram distribuídos.


### Configurar um Link de aplicativo

1. Para configurar os Links de aplicativo no aplicativo Android, acesse [Adicionar Links de aplicativo Android](https://developer.android.com/studio/write/app-link-indexing).

1. No Adobe Mobile Services, configure os documentos de associação ao site:

   a. Na página inicial do Mobile Services, selecione o aplicativo para o qual deseja configurar Links universais.

   b. Clique em **[!UICONTROL Gerenciar configurações do aplicativo]**.

   c. Adicione o aplicativo Android que processa links universais ou links de aplicativos na seção **[!UICONTROL Adicionar aplicativos da loja de aplicativos]**.

   >[!TIP]
   >
   >Se esta seção não foi exibida, clique no link **[!UICONTROL Adicionar aplicativo da loja de aplicativos]**.

   d. Role até a seção **[!UICONTROL Opções de links universais e links de aplicativos]**.

   e. Clique na guia **[!UICONTROL Links de aplicativo (Android)]**.

   f. Selecione um aplicativo Android e digite uma impressão digital de certificado SHA-256.

   g. Clique em **[!UICONTROL Salvar]**.

   Você deve fornecer pelo menos uma seleção de aplicativo Android e um certificado SHA-256, ou receberá um erro.

   >[!IMPORTANT]
   >
   >Você pode atualizar os documentos clicando em **[!UICONTROL Atualizar]** na seção **[!UICONTROL opções de Links Universais e Links de Aplicativo]**. Porém, quando você clica em **[!UICONTROL Atualizar]**, um aviso notifica que todos os Links universais ou de aplicativos que você criou no passado serão afetados.

### Usar um link de aplicativo

1. No Adobe Mobile Services, crie um Link de marketing que use Links de aplicativo:

   a. Selecione o aplicativo na página inicial do Mobile Services, clique em **[!UICONTROL Aquisição]** > **[!UICONTROL Construtor do Link de marketing]**.

   b. Clique em **[!UICONTROL Criar novo]**.

   c. Na seção **[!UICONTROL Opções de link de marketing]**, selecione **[!UICONTROL Usar links universais ou links de aplicativos]**.

   d. Se você tiver configurado os documentos de associação ao site desde a etapa 2, esta opção fica marcada por padrão.

   Senão, a opção **[!UICONTROL Usar Links universais ou Links de aplicativo]** estará desativado e **[!UICONTROL Usar intersticiais]** será selecionado por padrão.

   e. Se **[!UICONTROL Usar links universais ou links de aplicativos]** estiver selecionado, o campo **[!UICONTROL Caminho personalizado]** será exibido.

   Isso permite que os usuários definam o caminho do URL após o domínio com qualquer parâmetro de consulta. Por exemplo, se você digitar   `my/app/link?os=6.0`, seu URL completo do Link de marketing se torna `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Clique na guia **[!UICONTROL Decisões]** e configure sua árvore decisória.

   g. Se o aplicativo iOS estiver instalado, o aplicativo processará o link profundo de acordo com sua lógica.

   O destino final serve apenas como caso de fallback para quando o aplicativo não estiver instalado. Como o aplicativo não está instalado, o destino final só pode ser um link da Web ou uma loja de aplicativos.

   h. Clique em **[!UICONTROL Salvar]**.

>[!TIP]
>
>Depois que um Link de marketing é salvo, as **[!UICONTROL Opções de Links de marketing]** não podem ser alteradas. Isso ocorre porque você não é desejável alterar o comportamento dos Links de marketing que já foram distribuídos.

## Usar Links de marketing

Agora você pode usar esses Links de marketing em mensagens e outras áreas do aplicativo.

>[!IMPORTANT]
>
>Você não verá as contagens de rastreamento de cliques com Links Universais ou Links de Aplicativo, e também não poderá usar intersticiais.

