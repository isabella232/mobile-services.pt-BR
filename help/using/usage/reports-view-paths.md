---
description: O relatório Caminhos de exibição, que se baseia na análise de caminhos, mostra um gráfico que representa os caminhos que foram tomados entre estados no aplicativo.
keywords: mobile
seo-description: O relatório Caminhos de exibição, que se baseia na análise de caminhos, mostra um gráfico que representa os caminhos que foram tomados entre estados no aplicativo.
seo-title: Exibir relatório Caminhos
solution: Marketing Cloud,Analytics
title: Exibir relatório Caminhos
topic: Relatórios, Métricas
uuid: bc73edce-0cc0-4349-9a48-e0a40cbe1b67
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Exibir relatório Caminhos {#view-paths}

O relatório **[!UICONTROL Caminhos de exibição], que se baseia na análise de caminhos, mostra um gráfico que representa os caminhos que foram tomados entre estados no aplicativo.**

>[!TIP]
>
>The **[!UICONTROL View Paths]** and **[!UICONTROL View Action]** reports are similar because both are pathing reports. O relatório **[!UICONTROL Caminhos de exibição]permite ver como os usuários navegam no seu aplicativo de uma tela para outra.** O relatório **[!UICONTROL Ações de exibição]exibe a sequência de ações (eventos, como cliques, seleções, redimensionamento, etc.) que os usuários executam no aplicativo.** Você pode usar um relatório de funil para combinar navegação e ações em um relatório. Para obter mais informações, consulte [Funil](/help/using/usage/reports-funnel.md).

![visualizar caminhos](assets/view_paths.png)

Cada nó, formado como uma caixa, representa um estado nos caminhos dos usuários em um aplicativo. Por exemplo, na ilustração acima, o nó superior representa o número de usuários que inicializaram o aplicativo e navegaram até a exibição principal.

Quando você clica em um nó para fornecer as opções adicionais para modificar o gráfico, opções adicionais como **[!UICONTROL Focar]** ou **Expandir]são exibidas.[!UICONTROL ** Por exemplo, se você clicar no estado **[!UICONTROL MainView]** no nó superior, os ícones **[!UICONTROL Focar]e** Expandir] serão exibidos.**[!UICONTROL **

To expand the view, click the **[!UICONTROL +]** icon to display the additional paths that come in to or go from the node. Na ilustração abaixo, o estado 1 é a inicialização do aplicativo, o estado 2 é a visualização da página principal do aplicativo e o estado 3 inclui os seguintes caminhos que os usuários tomaram:

* Navegando até o rolo da câmera
* navegando até o seletor de itens
* navegando até a câmera
* navegando para a página de informações do item

![](assets/view_paths_expand.png)

Click ![focus icon](assets/icon_focus.png) to isolate the node and to show the paths that are coming into and going out of the selected node. Na ilustração abaixo, os seguintes caminhos precederam os usuários que estavam vendo a exibição principal do aplicativo:

* informações do item
* seletor de item
* Rolo da câmera
* Câmera

![visualizar foco do caminho](assets/view_paths_focus.png)

Você pode focar ou expandir vários nós para uma exibição detalhada dos caminhos que os usuários tomaram no aplicativo. Por exemplo:

![caminho de visualização múltiplo](assets/view_paths_mult.png)

Você pode configurar as seguintes opções no relatório:

* **[!UICONTROL Período]** Clique no ícone **[!UICONTROL Calendário]** para selecionar um período personalizado ou para selecionar um período predefinido na lista suspensa.
* **[!UICONTROL Personalizar]** Personalize seus relatórios alterando as opções **[!UICONTROL Mostrar por]** , adicionando métricas e filtros e adicionando outras séries (métricas) e muito mais. For more information, see [Customize Reports](/help/using/usage/reports-customize/reports-customize.md).
* **[!UICONTROL Filtrar]** Clique em **[!UICONTROL Filtro]** para criar um filtro que abrange diferentes relatórios para ver como um segmento está se saindo em todos os relatórios móveis. Um filtro fixo permite definir um filtro aplicado a todos os relatórios não relacionados à definição de caminho. Para obter mais informações, consulte [Adicionar filtro](/help/using/usage/reports-customize/t-sticky-filter.md)fixo.
* **[!UICONTROL Download]** Clique em **[!UICONTROL PDF]** ou **[!UICONTROL CSV]** para baixar ou abrir documentos e compartilhar com usuários que não têm acesso ao Mobile Services ou para usar o arquivo em apresentações.