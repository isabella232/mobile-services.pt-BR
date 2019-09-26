---
description: Conclua essas etapas a fim de configurar um conjunto de relatórios para coletar dados de aplicativos do iOS.
seo-description: Conclua essas etapas a fim de configurar um conjunto de relatórios para coletar dados de aplicativos do iOS.
seo-title: Antes de começar
solution: Marketing Cloud,Analytics
title: Antes de começar
topic: Desenvolvedor e implementação
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Before you start {#before-you-start}

Conclua essas etapas a fim de configurar um conjunto de relatórios para coletar dados de aplicativos do iOS.

## Role-specific tasks {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Os administradores do Analytics e desenvolvedores de aplicativos devem realizar as seguintes tarefas:

### Administradores do Analytics

Para configurar um conjunto de relatórios e coletar dados do aplicativo móvel:

1. Conclua uma das seções em [Fazer logon na interface do usuário do Adobe Mobile Services](/help/ios/getting-started/getting-started.md).
1. Crie uma conta do Analytics para cada desenvolvedor de aplicativos.

Os desenvolvedores de aplicativos agora têm acesso para visualizar o(s) conjunto(s) de relatórios criados por você.

>[!IMPORTANT]
>
>Para criar um novo conjunto de relatórios e baixar os SDKs, você deve ser um Administrador do Analytics.

### Desenvolvedores do aplicativo

1. Ensure that your Analytics administrator has completed the steps in the *Analytics Administrators* section above.

1. Verify that your Analytics administrator has completed one of the sections in the *Log in to the Adobe Mobile Services UI* below.
1. After the report suite has been configured, complete steps in the *Download the SDK* section below.

Para obter mais informações sobre funções e permissões, consulte [Funções e permissões](/help/using/gs/c-mob-roles-and-permissions.md).

## Fazer logon na interface do usuário do Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Os Adobe Mobile Services são a principal interface de relatórios para análise e segmentação de aplicativos móveis. Depois de concluir estas etapas, você pode baixar um arquivo de configuração pré-configurado com seu servidor de coleta de dados, conjunto de relatórios e muitas outras configurações.

É possível fazer logon no Adobe Mobile Services de uma das seguintes maneiras:

* **Experience Cloud**

   Faça logon na [Experience Cloud](https://marketing.adobe.com) com sua Adobe ID.

   Esse método presume que sua empresa foi provisionada e que você vinculou sua conta do Analytics. For more information about provisioning, see Manage Experience Cloud users and products. [](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html) For more information about linking your account, see Organizations and account linking.[](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html)

   >[!TIP]
   >
   >Se não tiver certeza se sua empresa foi provisionada na Experience Cloud, use sua conta existente do Adobe Analytics.

* **Adobe Analytics**

   Clique em **[!UICONTROL Fazer logon com o Analytics]** e digite o nome da empresa do Analytics, o nome de usuário e a senha.

## Criar um novo conjunto de relatórios {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Para criar um conjunto de relatórios para coletar dados do aplicativo e definir um aplicativo:

1. Clique em **[!UICONTROL Criar novo aplicativo]**.

   If you do not see this button, click **[!UICONTROL Manage Apps]** &gt; **[!UICONTROL Add]**.

1. No menu suspenso **[!UICONTROL Conjunto de relatórios]**, selecione **[!UICONTROL Novo conjunto de relatórios]**.

1. Digite o nome do aplicativo e selecione uma ID de conjunto de relatórios exclusiva.

   Um exemplo de uma ID de conjunto de relatórios é `mycomobileappdev`. You need to set up separate report suites and apps for the development and production versions. When you are ready to set up the production version, repeat these steps.
1. Deixe **[!UICONTROL Modelo de aplicativo móvel]selecionado.**

   Este modelo permite que os carimbos de data e hora coletem dados offline e ativem as variáveis da solução móvel para capturar medições de ciclo de vida.

1. Select your **[!UICONTROL Timezone]**, your **[!UICONTROL Currency]**, and click **[!UICONTROL Save]**.

## Baixar o SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Para baixar o SDK móvel:

1. Faça logon no Mobile Services e abra seu aplicativo de uma das seguintes maneiras:

   * Na lista suspensa **[!UICONTROL Todos os aplicativos], selecione o aplicativo.**
   * No painel direito, encontre seu aplicativo e abra-o.

1. Clique em **[!UICONTROL Gerenciar configurações do aplicativo]**.
1. Na seção **[!UICONTROL Downloads de SDK de aplicativos]**, navegue até a seção **Downloads de SDK de aplicativos[!UICONTROL .]**

1. Baixe o SDK e do aplicativo de exemplo para a sua plataforma.

>[!TIP]
>
>Um arquivo de configuração para seu aplicativo é incluído automaticamente no download do SDK, portanto, não é necessário baixar esse arquivo separadamente. No entanto, se já tiver baixado o SDK e deseja obter configurações atualizadas, baixe o arquivo de configuração novamente.

