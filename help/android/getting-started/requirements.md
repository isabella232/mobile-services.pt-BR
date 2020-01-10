---
description: 'Antes de configurar um conjunto de relatórios e coletar os dados de aplicativo do Android, complete as seguintes tarefas de pré-requisitos '
seo-description: 'Antes de configurar um conjunto de relatórios e coletar os dados de aplicativo do Android, complete as seguintes tarefas de pré-requisitos '
seo-title: Antes de começar
solution: Marketing Cloud,Analytics
title: Antes de começar
topic: Developer and implementation
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
translation-type: tm+mt
source-git-commit: 0720b2004097eb288bd8f59723eeb09a79dd81e7

---


# Antes de começar {#before-you-start}

Antes de configurar um conjunto de relatórios e coletar os dados de aplicativo do Android, complete as seguintes tarefas de pré-requisitos:

## Tarefas com função específica {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Os administradores do Analytics e desenvolvedores de aplicativos devem realizar as seguintes tarefas:

### Administradores do Analytics

Para configurar um conjunto de relatórios e coletar dados do aplicativo móvel:

1. Conclua uma das seções em [Fazer logon na interface do usuário do Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Crie uma conta do Analytics para cada desenvolvedor de aplicativos.

Os desenvolvedores de aplicativos agora têm acesso para visualizar o(s) conjunto(s) de relatórios criados por você.

>[!IMPORTANT]
>
>Para criar um novo conjunto de relatórios e baixar os SDKs, é necessário ser administrador do Analytics.

### Desenvolvedores do aplicativo

1. Ensure that your Analytics administrator has completed the steps in the *Analytics Administrators* in [Role-Specific Tasks](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC).
1. Verifique se o administrador do Analytics concluiu uma das seções em [Fazer logon na interface do usuário do Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. After the report suite has been configured, complete steps in the [Download the SDK](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46).

Para obter mais informações sobre funções e permissões, consulte [Funções e permissões](/help/using/gs/c-mob-roles-and-permissions.md).

## Fazer logon na interface do usuário do Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

O Adobe Mobile Services é a principal interface de relatórios para análise e segmentação de aplicativos móveis. Após concluir estas etapas, é possível baixar um arquivo de configuração pré-configurado com seu servidor de coleta de dados, conjunto de relatórios e muitas outras configurações.

É possível fazer logon na interface do usuário do Adobe Mobile Services por meio de uma das maneiras a seguir:

### Experience Cloud

Faça logon na [Experience Cloud](https://marketing.adobe.com) com sua Adobe ID. Esse método entende que sua empresa foi provisionada na Experience Cloud e que você vinculou sua conta do Analytics. Para obter mais informações, consulte [Gerenciar usuários e produtos da Experience Cloud](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>Se não tiver certeza se sua empresa foi provisionada na Experience Cloud, use a conta existente do Adobe Analytics.

### Adobe Analytics

Clique em **[!UICONTROL Fazer logon com o Analytics]** e digite o nome da empresa do Analytics, o nome de usuário e a senha.

## Criar um novo conjunto de relatórios {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Para criar um conjunto de relatórios para coletar dados do aplicativo e definir um aplicativo:

1. Faça logon na interface do usuário do Mobile Services digitando [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) em um navegador.
1. Click **[!UICONTROL Create an App]**.

   Se não vir este botão, clique em **[!UICONTROL Gerenciar aplicativos]** > **[!UICONTROL  Adicionar]**.

1. No menu suspenso **[!UICONTROL Conjunto de relatórios]**, selecione **[!UICONTROL  Novo conjunto de relatórios]**.

1. Digite o nome do aplicativo e selecione um tipo de conjunto de relatórios.

   Um exemplo de uma ID de conjunto de relatórios é `mycomobileappdev`. É necessário definir conjuntos de relatórios e aplicativos separados das versões de desenvolvimento e produção, de forma que possa repetir essas etapas quando estiver pronto para configurar a versão de produção.
1. Em **[!UICONTROL ID de conjunto de relatórios]**, verifique se o nome do seu conjunto de relatórios é exibido.
1. Em **[!UICONTROL Copiar configurações de]**, verifique se **[!UICONTROL  Modelo de aplicativo móvel]** está selecionado.

   Este modelo permite que os carimbos de data e hora coletem dados offline e ativem as variáveis da solução móvel para capturar medições de ciclo de vida.

1. Selecione o fuso horário, a moeda e clique em **[!UICONTROL Salvar]**.

## Baixar o SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Para baixar o SDK móvel:

1. faça logon na interface do usuário do Mobile Services digitando [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) em um navegador.
1. No painel esquerdo, clique na lista suspensa **[!UICONTROL Todos os aplicativos]** e selecione seu aplicativo.
Você também pode selecionar seu aplicativo no painel direito.

   >[!IMPORTANT]
   >
   >Para ver seu aplicativo exibido no painel direito, primeiro crie um aplicativo. Para obter informações sobre como criar um aplicativo, consulte [Adicionar um novo aplicativo.](https://docs.adobe.com/content/help/en/mobile-services/using/manage-apps-ug/t-new-app.html)

1. No aplicativo, no painel esquerdo, clique em **[!UICONTROL Gerenciar configurações]** do aplicativo.

   >[!IMPORTANT]
   >
   >Se não vir a opção **[!UICONTROL Gerenciar configurações]** do aplicativo, verifique se você está conectado ao Adobe Mobile Services. Para verificar, clique no ícone do alternador ![de](assets/solution-switcher.png)soluções no lado superior direito da página e verifique se o **[!UICONTROL  Adobe Mobile Services]** é exibido no lado superior esquerdo.

1. Na parte inferior da página Gerenciar configurações do aplicativo, na seção Downloads **[!UICONTROL do SDK do]** aplicativo, baixe o SDK e o aplicativo de amostra para sua plataforma.

>[!TIP]
>
>Um arquivo de configuração para o seu aplicativo é incluído automaticamente no download do SDK; portanto, você não precisa baixar esse arquivo separadamente. No entanto, se já tiver baixado o SDK e deseja obter configurações atualizadas, baixe o arquivo de configuração novamente.

Se você usa o Android Studio, também é possível adicionar o seguinte código ao arquivo `build.gradle` do seu aplicativo:

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

Lembre-se das seguintes informações:

* Substitua o número da versão na amostra de código pela versão apropriada dos Android SDKs.
* Baixe o arquivo de configuração e inclua-o em seu projeto.
