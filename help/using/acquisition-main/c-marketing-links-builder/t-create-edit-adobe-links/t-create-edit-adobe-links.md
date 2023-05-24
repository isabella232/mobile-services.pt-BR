---
description: É possível criar ou editar links de marketing para incluir links profundos no seu aplicativo móvel ou site.
keywords: dispositivos móveis
solution: Experience Cloud Services,Analytics
title: Criar ou editar links de marketing
topic-fix: Metrics
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
exl-id: a9b5c98d-77c1-4a40-96e5-f9e234d55ec5
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 98%

---

# Criar ou editar links de marketing {#create-or-edit-marketing-links}

{#eol}

É possível criar ou editar links de marketing para incluir links profundos no seu aplicativo móvel ou site. Para obter mais informações, consulte [Links universais da Apple e Links de aplicativos Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. No seu aplicativo, no painel de navegação esquerdo, clique em **[!UICONTROL Aquisição]** e em **[!UICONTROL Construtor de links de marketing]**.
1. Conclua uma das seguintes tarefas:

   * Para criar um novo link de marketing, clique em **[!UICONTROL Criar novo]**.
   * Para editar um link, clique no nome do link na coluna **[!UICONTROL Título]**.

1. Digite informações nos seguintes campos:

   * **[!UICONTROL Nome do link de marketing]**:

      (**Obrigatório**) Especifique um nome descritivo para o link de marketing. O nome é exibido somente na página links de publicidade na interface do usuário do Adobe Mobile Services. Um nome descritivo ajuda você ou outras pessoas na sua organização a encontrar rapidamente um link específico e pode fornecer informações sobre a sua finalidade.

   * **[!UICONTROL Código de rastreamento exclusivo]**:

      (**Obrigatório**) Especifique o código de rastreamento desejado ou clique em ( ![gerar ícone](assets/icon_generate.png) ) para criar um novo código de rastreamento. É possível exibir relatórios que detalham o uso do código de rastreamento.

   * **[!UICONTROL Adicionar dados de contexto de rastreamento]**:

      (**Opcional**) Clique no ícone **[!UICONTROL +]** e digite as informações relevantes para acompanhar sua campanha usando dados de contexto. Na lista suspensa **[!UICONTROL Dados contextuais personalizados]**, selecione uma tag predefinida ou uma de suas próprias tags. Os dados de contexto são usados para informar quando o link de marketing é implantado.

      As tags predefinidas a seguir estão disponíveis:

      * **Dados de contexto personalizados**
Especifique a chave e o valor. Se você adicionar dados de contexto personalizados, é necessário criar uma regra de processamento. Para obter mais informações, consulte [Visão geral das regras de processamento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html?lang=pt-BR) na documentação do Adobe Analytics.

      * **Fonte**
Especifique o referenciador original, por exemplo, “boletim informativo” ou “página inicial”.

      * **Meio**
Especifique o meio de marketing, por exemplo, “banner” ou “email”.

      * **Conteúdo**
Especifique o nome ou a ID do anúncio com o link.

      * **Termo**
Especifique os termos de pagamento ou outros termos de pesquisa para o anúncio.
1. Clique em **[!UICONTROL Salvar]**.
1. Digite informações nos seguintes campos:

   * **(Obrigatório)** Em **[!UICONTROL URL de fallback]**, especifique o URL ao qual os usuários são direcionados quando um destino não pode ser correspondido (por exemplo, se o usuário estiver em um desktop ou outra plataforma que não corresponde a uma regra de destino).
   * Nas **[!UICONTROL Opções de link de marketing]**, selecione **[!UICONTROL Intersticiais]** ou **[!UICONTROL Links universais e de aplicativos]**.

      Para obter mais informações, consulte [Intersticiais](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) ou [Links universais da Apple e Links de aplicativos Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

   * **(Condicional)** Se os **[!UICONTROL Links universais ou de aplicativos]** forem selecionados, os usuários poderão definir, em **[!UICONTROL Caminho personalizado]**, o caminho do URL após o domínio com qualquer parâmetro de consulta. Para obter mais informações, consulte [Links universais da Apple e Links de aplicativos Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. Clique em **[!UICONTROL Editar link profundo intersticial]** e configure o link.

   (**Opcional**) Quando existem vários destinos, os usuários que têm ou não aplicativo móvel instalado podem ser encaminhados conforme o caso. Se o aplicativo estiver instalado, uma página de destino intersticial será exibida.

   Para obter mais informações, consulte [Intersticial](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. Clique em **[!UICONTROL Salvar]** e clique em **[!UICONTROL Próximo]**.
1. Na página Destino, configure o link.

   1. Clique no ícone **[!UICONTROL Decisão]** ( ![decision icon](assets/icon_decision.png) ) e selecione um dos seguintes locais de decisão:

      * **[!UICONTROL Adicionar decisão]**
      * **[!UICONTROL Adicionar caminho]**
   1. Se tiver selecionado **[!UICONTROL Adicionar decisão]**, selecione um dos seguintes tipos de decisão:

      * **[!UICONTROL Decisão operacional]**

         Os sistemas operacionais suportados incluem iOS, Android, AMX, e assim por diante.

      * **[!UICONTROL Device Type]**

         Os tipos de dispositivos incluem dispositivos como desktops, eReaders, consoles de jogos, telefones celulares, set top boxes, e assim por diante.
   1. Clique no ícone **[!UICONTROL Destino]** ( ![square icono](assets/icon_square.png) ) e selecione um dos seguintes tipos de destino:

      * **[!UICONTROL Loja de aplicativos]**
      * **[!UICONTROL Link da Web]**
      * **[!UICONTROL Deep link do aplicativo]**
      * **[!UICONTROL Link híbrido]**

      >[!TIP]
      >
      >Se você usar os tipos de destino **[!UICONTROL Link da Web]** com um link para a loja de aplicativos, a aquisição não é rastreada. Para rastrear as aquisições, use o tipo de destino da **[!UICONTROL App Store]**.

      Para obter mais informações, consulte [Criar um novo destino de link](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md).




1. Para salvar o Link de marketing, clique em ![elipses](assets/icon_elipses.png) e depois em **[!UICONTROL Salvar]**.
