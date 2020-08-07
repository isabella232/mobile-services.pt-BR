---
description: É possível usar estas informações para criar um novo aplicativo e configurar suas métricas principais; configurar as opções do SDK para o Adobe Analytics e o Adobe Audience Manager; configurar as opções de aquisição e de serviço de ID; e baixar o arquivo de configuração, os SDKs e as ferramentas de desenvolvedor e de testador.
keywords: mobile
seo-description: É possível usar estas informações para criar um novo aplicativo e configurar suas métricas principais; configurar as opções do SDK para o Adobe Analytics e o Adobe Audience Manager; configurar as opções de aquisição e de serviço de ID; e baixar o arquivo de configuração, os SDKs e as ferramentas de desenvolvedor e de testador.
seo-title: Adicionar um novo aplicativo
solution: Marketing Cloud,Analytics
title: Adicionar um novo aplicativo
topic: Metrics
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 95%

---


# Adicionar um novo aplicativo{#add-a-new-app}

É possível usar estas informações para criar um novo aplicativo e configurar suas métricas principais; configurar as opções do SDK para o Adobe Analytics e o Adobe Audience Manager; configurar as opções de aquisição e de serviço de ID; e baixar o arquivo de configuração, os SDKs e as ferramentas de desenvolvedor e de testador.

Essas instruções ajudarão você a adicionar um novo aplicativo e configurar as integrações do Adobe Analytics e do Adobe Audience Manager.

Antes de configurar seu aplicativo, você deve adicioná-lo na interface do usuário do Adobe Mobile Services. Depois de criar o aplicativo, a configuração correta é gerada e você pode fornecer essa configuração aos desenvolvedores que estão implementando o SDK móvel para o aplicativo.

1. Faça logon no Adobe Mobile Services e realize uma das seguintes tarefas:

   * Clique em **[!UICONTROL Criar novo]** para criar um aplicativo.
   * Para adicionar outros aplicativos, clique em Gerenciar aplicativos no menu de navegação esquerdo e clique em **[!UICONTROL Adicionar]**.

      Para obter mais informações sobre como fazer logon, consulte [Fazer logon](/help/using/gs/gs-signin.md).

      >[!TIP]
      >
      >Para gerenciar os aplicativos existentes, clique em Gerenciar aplicativos no menu de navegação esquerdo e clique no aplicativo que deseja modificar. Você pode fazer alterações na página Informações do aplicativo.

1. Digite informações nos seguintes campos:

   **[!UICONTROL Conjunto de relatórios]**

   Especifique o conjunto de relatórios no qual os dados de relatório serão coletados e armazenados no Adobe Analytics. Cada aplicativo está conectado a um único conjunto de relatórios do Analytics. Caso esteja enviando dados do aplicativo para vários conjuntos de relatórios, adicione um novo aplicativo para cada conjunto de relatórios. Cada aplicativo está conectado a um único conjunto de relatórios do Analytics. Caso esteja enviando dados do aplicativo para vários conjuntos de relatórios, adicione um novo aplicativo para cada conjunto de relatórios.

   Se tiver recebido privilégios de administrador do Analytics no Adobe Mobile, você pode criar um novo conjunto de relatórios no Adobe Mobile. Para criar um novo conjunto de relatórios, selecione **[!UICONTROL Novo conjunto de relatórios]** e digite as informações nos seguintes campos:

   * **[!UICONTROL ID de conjunto de relatórios]**

      Essa ID identifica exclusivamente o conjunto de relatórios no Adobe Analytics. O prefixo da sua empresa é adicionado automaticamente ao início da ID.

   * **[!UICONTROL Copiar configurações de]**

      As variáveis, os eventos, as regras de processamento e outras configurações são ajustadas no novo conjunto de relatórios exatamente como estão neste conjunto de relatórios. Um conjunto de relatórios criado no Mobile Services é habilitado para ser usado offline (ou carimbado com data/hora) apenas se o conjunto de relatórios **[!UICONTROL Copiar configurações de]** que foi usado tiver sido o Modelo de aplicativo móvel, ou caso você tenha criado um conjunto de relatórios habilitado para ser usado offline.

   * **[!UICONTROL Fuso horário]**

      Todas as datas dos relatórios estão no mesmo fuso horário. Essa configuração tenta usar um fuso horário próximo ao do seu navegador.

   * **[!UICONTROL Moeda]**

      A receita é verificada e relatado com esse tipo de moeda.
   >[!TIP]
   >
   >Para usar um conjuntos de relatórios virtuais (VRS), consulte [Conjuntos de relatórios virtuais](/help/using/manage-apps/c-mob-vrs.md).

   * **[!UICONTROL Ícone]**

      (**Opcional**) Para navegar até um ícone e selecioná-lo para o seu aplicativo, clique no **[!UICONTROL ícone]**.

   * **[!UICONTROL Nome]**

      (**Opcional**) Digite um nome descritivo para o aplicativo. Este nome o ajuda a localizar um aplicativo rapidamente, e um nome significativo pode ajudá-lo a entender o propósito e as configurações do aplicativo.

   * **[!UICONTROL Tipo]**

      Selecione um tipo na lista suspensa. Os relatórios disponíveis exibidos no menu de navegação esquerdo variam dependendo do tipo de aplicativo selecionado.

      Estes são os tipos disponíveis:

      * **[!UICONTROL Padrão]**

         É possível deixar a opção **[!UICONTROL Padrão}** selecionada para a maioria dos aplicativos.

      * **[!UICONTROL Publicação]**

         Você pode selecionar esta opção se seu aplicativo foi criado usando o Adobe Digital Publishing Suite.

      * **[!UICONTROL Jogo]**

         Esta opção é semelhante à opção **[!UICONTROL Padrão]**, exceto que **[!UICONTROL Jogo]** atualiza a terminologia usada nos relatórios para termos de jogos. Por exemplo, a terminologia usuários é alterada para jogadores. Relatórios específicos para jogos são exibidos automaticamente para aplicativos de jogos.
   * **[!UICONTROL Descrição]**

      (**Opcional**) Digite uma descrição para o aplicativo.



1. Clique em **[!UICONTROL Salvar]** para adicionar o novo aplicativo.

   Após a adição do aplicativo, você pode verificar a página Informações do aplicativo sobre a configuração de opções adicionais. Para obter mais informações, consulte [Gerenciar configurações do aplicativo](/help/using/c-manage-app-settings/c-manage-app-settings.md).
