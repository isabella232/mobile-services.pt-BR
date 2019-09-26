---
description: Você pode criar ou editar links de marketing para fornecer deep links ao seu aplicativo móvel ou site.
keywords: mobile
seo-description: Você pode criar ou editar links de marketing para fornecer deep links ao seu aplicativo móvel ou site.
seo-title: Criar ou editar links de publicidade
solution: Marketing Cloud,Analytics
title: Criar ou editar links de publicidade
topic: Métricas
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Create or edit marketing links{#create-or-edit-marketing-links}

Você pode criar ou editar links de marketing para fornecer deep links para seu aplicativo móvel ou site. Para obter mais informações, consulte Links universais [da Apple e Links](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)de aplicativos Android.

1. In your app, in the left navigation pane, expand **[!UICONTROL Acquisition]** and click **[!UICONTROL Marketing Link Builder]**.
1. Conclua uma das seguintes tarefas:

   * To create a Marketing Link, click **[!UICONTROL Create New]**.
   * Para editar um link, clique no nome do link na coluna **[!UICONTROL Título].**

1. Digite informações nos seguintes campos:

   * **[!UICONTROL Nome do link de marketing]**:

      (**Required**) Specify a descriptive name for your Marketing Link. O nome é exibido somente na página links de publicidade na interface do usuário do Adobe Mobile Services. Um nome descritivo ajuda você ou outras pessoas na sua organização a encontrar rapidamente um link específico e pode fornecer informações sobre a sua finalidade.

   * **[!UICONTROL Código de rastreamento exclusivo]**:

      (**Required**) Specify the desired tracking code or click (![generate icon](assets/icon_generate.png) to create a new tracking code. É possível exibir relatórios que detalham o uso do código de rastreamento.

   * **[!UICONTROL Adicionar dados de contexto de rastreamento]**:

      (**Optional**) Click the **[!UICONTROL +]** icon and type the relevant information to track your campaign using context data. Na lista suspensa **[!UICONTROL Dados contextuais personalizados], selecione uma tag predefinida ou uma de suas próprias tags.** Context data is used for reporting when the Marketing Link is deployed.

      As tags predefinidas a seguir estão disponíveis:

      * **Dados** de contexto personalizados Especifique a chave e o valor. Se você adicionar dados de contexto personalizados, é necessário criar uma regra de processamento. Para obter mais informações, consulte Visão geral [das regras de](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)processamento.

      * **Fonte** Especifique o referenciador original, como "boletim informativo" ou "página inicial".

      * **Médio** Especifique a mídia de marketing, como "banner" ou "email".

      * **Conteúdo** Especifique o nome ou a ID do anúncio com o link.

      * **Termo** Especifique os termos pagos ou outros termos de pesquisa para o anúncio.
1. Clique em **[!UICONTROL Salvar]**.
1. Digite informações nos seguintes campos:

   * **(Obrigatório)** No URL **[!UICONTROL de]** Fallback, especifique o URL ao qual os usuários são direcionados quando um destino não pode ser correspondido (por exemplo, se o usuário estiver em um desktop ou outra plataforma que não corresponda a uma regra de destino).
   * In **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Interstitials]** or **[!UICONTROL Universal and App Links]**.

      Para obter mais informações, consulte [Intersticiais](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) ou Links [universais da Apple e Links](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)de aplicativos Android.

   * **(Condicional)** Se **[!UICONTROL Universal ou Links]** de aplicativo estiver selecionado, em Caminho **** personalizado, os usuários poderão definir o caminho do URL após o domínio com qualquer parâmetro de consulta. Para obter mais informações, consulte Links universais [da Apple e Links](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)de aplicativos Android.

1. Click **[!UICONTROL Edit Deep Link Interstitial]** and configure the link.

   (**Optional**) When there are multiple destinations, users can be routed depending on whether they have a mobile app installed. Se o aplicativo estiver instalado, uma página de destino intersticial será exibida.

   Para obter mais informações, consulte [Intersticiais](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. Click **[!UICONTROL Save]** and click **[!UICONTROL Next]**.
1. Na página Destino, configure o link.

   1. Click the **[!UICONTROL Decision]** icon (![decision icon](assets/icon_decision.png)) and select one of the following decision locations:

      * **[!UICONTROL Adicionar decisão]**
      * **[!UICONTROL Adicionar caminho]**
   1. If you selected **[!UICONTROL Add Decision]**, select one of the following decision types:

      * **[!UICONTROL Decisão operacional]**

         Os sistemas operacionais suportados incluem iOS, Android, AMX, e assim por diante.

      * **[!UICONTROL Tipo de dispositivo]**

         Os tipos de dispositivos incluem dispositivos como desktops, eReaders, consoles de jogos, telefones celulares, set top boxes, e assim por diante.
   1. Click the **[!UICONTROL Destination]** icon ( ![square icon](assets/icon_square.png) ) and select one of the following destination types:

      * **[!UICONTROL App Store]**
      * **[!UICONTROL Link da Web]**
      * **[!UICONTROL Deep link do aplicativo]**
      * **[!UICONTROL Link híbrido]**
      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** destination type with a link to the app store, acquisition is not tracked. Para rastrear as aquisições, use o tipo de destino da **[!UICONTROL App Store].**

      Para obter mais informações, consulte [Criar um novo destino](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md)de link.




1. Para salvar o Link de marketing, clique em ![exclusões](assets/icon_elipses.png) e em **[!UICONTROL Salvar]**.
