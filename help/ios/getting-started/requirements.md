---
description: Conclua essas etapas a fim de configurar um conjunto de relatórios para coletar dados de aplicativos do iOS.
seo-description: Conclua essas etapas a fim de configurar um conjunto de relatórios para coletar dados de aplicativos do iOS.
seo-title: Antes de começar
solution: Experience Cloud,Analytics
title: Antes de começar
topic: Developer and implementation
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 100%

---


# Antes de começar {#before-you-start}

Conclua essas etapas a fim de configurar um conjunto de relatórios para coletar dados de aplicativos do iOS.

## Tarefas com função específica {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Os administradores do Analytics e desenvolvedores de aplicativos devem realizar as seguintes tarefas:

### Administradores do Analytics

Para configurar um conjunto de relatórios e coletar dados do aplicativo móvel:

1. Conclua uma das seções em [Fazer logon na interface do usuário do Adobe Mobile Services](/help/ios/getting-started/getting-started.md).
1. Crie uma conta do Analytics para cada desenvolvedor de aplicativos.

Os desenvolvedores de aplicativos agora têm acesso à visualização dos conjuntos de relatórios criados.

>[!IMPORTANT]
>
>Para criar um novo conjunto de relatórios e baixar os SDKs, é necessário ser administrador do Analytics.

### Desenvolvedores do aplicativo

1. Certifique-se de que o administrador do Analytics concluiu as etapas da seção *Administradores do Analytics* disponível acima.

1. Verifique se o administrador do Analytics concluiu uma das seções em *Fazer logon na interface do Adobe Mobile Services*.
1. Após a configuração do conjunto de relatórios, conclua as etapas da seção *Baixar o SDK* disponível abaixo.

Para obter mais informações sobre funções e permissões, consulte [Funções e permissões](/help/using/gs/c-mob-roles-and-permissions.md).

## Fazer logon na interface do usuário do Adobe Mobile Services   {#section_690A2EC4572E47869F183974E932A6A8}

O Adobe Mobile Services é a principal interface de relatórios para análise e direcionamento de aplicativos móveis. Após concluir essas etapas, é possível baixar um arquivo de configuração pré-configurado com seu servidor de coleta de dados, conjunto de relatórios e muitas outras configurações.

Você pode fazer logon no Adobe Mobile Services de uma das seguintes maneiras:

* **Experience Cloud**

   Faça logon na [Experience Cloud](https://marketing.adobe.com) com sua Adobe ID.

   Esse método pressupõe que sua empresa foi provisionada e que você vinculou sua conta do Analytics. Para obter mais informações sobre o provisionamento, consulte [Gerenciar usuários e produtos da Experience Cloud](https://docs.adobe.com/content/help/pt-BR/core-services/interface/manage-users-and-products/admin-getting-started.html). Para obter mais informações sobre como vincular sua conta, consulte [Vinculação de organizações e contas](https://docs.adobe.com/content/help/pt-BR/core-services/interface/manage-users-and-products/organizations.html).

   >[!TIP]
   >
   >Se não tiver certeza se sua empresa foi provisionada na Experience Cloud, use a conta existente do Adobe Analytics.

* **Adobe Analytics**

   Clique em **[!UICONTROL Fazer logon com o Analytics]** e digite o nome da empresa do Analytics, o nome de usuário e a senha.

## Criar um novo conjunto de relatórios {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Para criar um conjunto de relatórios para coletar dados do aplicativo e definir um aplicativo:

1. Clique em **[!UICONTROL Criar novo aplicativo]**.

   Se não vir este botão, clique em **[!UICONTROL Gerenciar aplicativos]** > **[!UICONTROL Adicionar]**.

1. No menu suspenso **[!UICONTROL Conjunto de relatórios]**, selecione **[!UICONTROL Novo conjunto de relatórios]**.

1. Digite o nome do aplicativo e selecione uma ID de conjunto de relatórios exclusiva.

   Um exemplo de uma ID de conjunto de relatórios é `mycomobileappdev`. É necessário configurar conjuntos de relatórios e aplicativos separados para as versões de desenvolvimento e de produção. Quando estiver pronto para configurar a versão de produção, repita essas etapas.
1. Deixe **[!UICONTROL Modelo de aplicativo móvel]** selecionado.

   Este modelo permite que os carimbos de data e hora coletem dados offline e ativem as variáveis da solução móvel para capturar medições de ciclo de vida.

1. Selecione o **[!UICONTROL Fuso horário]**, a **[!UICONTROL Moeda]** e clique em **[!UICONTROL Salvar]**.

## Baixar o SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Para baixar o SDK móvel:

1. Faça logon no Mobile Services e abra o aplicativo de uma das seguintes maneiras:

   * Na lista suspensa **[!UICONTROL Todos os aplicativos]**, selecione o aplicativo.
   * No painel direito, encontre seu aplicativo e abra-o.

1. Clique em **[!UICONTROL Gerenciar configurações do aplicativo]**.
1. Na seção **[!UICONTROL Downloads de SDK de aplicativos]**, navegue até a seção **[!UICONTROL Downloads de SDK de aplicativos]**.

1. Baixe o SDK e do aplicativo de exemplo para a sua plataforma.

>[!TIP]
>
>Um arquivo de configuração para o seu aplicativo é incluído automaticamente no download do SDK; portanto, você não precisa baixar esse arquivo separadamente. No entanto, se já tiver baixado o SDK e deseja obter configurações atualizadas, baixe o arquivo de configuração novamente.

