---
description: 'Antes de configurar um conjunto de relatórios e coletar os dados de aplicativo do Android, complete as seguintes tarefas de pré-requisitos '
seo-description: 'Antes de configurar um conjunto de relatórios e coletar os dados de aplicativo do Android, complete as seguintes tarefas de pré-requisitos '
seo-title: Antes de começar
solution: Marketing Cloud, Analytics
title: Antes de começar
topic: Desenvolvedor e implementação
uuid: 0 ca 9 e 937-8 d 40-4570-9 dbf -9 guidc 6 ecedf 6
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Before you start {#before-you-start}

Antes de configurar um conjunto de relatórios e coletar os dados de aplicativo do Android, complete as seguintes tarefas de pré-requisitos:

## Role-specific tasks {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Os administradores do Analytics e desenvolvedores de aplicativos devem realizar as seguintes tarefas:

### Administradores do Analytics

Para configurar um conjunto de relatórios e coletar dados do aplicativo móvel:

1. Conclua uma das seções em [Fazer logon na interface do usuário do Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Crie uma conta do Analytics para cada desenvolvedor de aplicativos.

Os desenvolvedores de aplicativos agora têm acesso para visualizar o(s) conjunto(s) de relatórios criados por você.

>[!IMPORTANT]
>
>Para criar um novo conjunto de relatórios e baixar os sdks, é necessário ser um Administrador do Analytics.

### Desenvolvedores do aplicativo

1. Assegure-se de que o administrador do Analytics concluiu as etapas na seção *Administradores do Analytics* em [Tarefas específicas por função](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC).

1. Verifique se o administrador do Analytics concluiu uma das seções em [Fazer logon na interface do usuário do Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Após o conjunto de relatórios ser configurado, conclua as etapas em [Baixar o SDK](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46).

Para obter mais informações sobre funções e permissões, consulte [Funções e permissões](/help/using/gs/c-mob-roles-and-permissions.md).

## Fazer logon na interface do usuário do Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

O Adobe Mobile Services é a principal interface de relatórios para análise e segmentação de aplicativos móveis. Após concluir estas etapas, é possível baixar um arquivo de configuração pré-configurado com seu servidor de coleta de dados, conjunto de relatórios e muitas outras configurações.

É possível fazer logon na interface do usuário do Adobe Mobile Services por meio de uma das maneiras a seguir:

### Experience Cloud

Faça logon na [Experience Cloud](https://marketing.adobe.com) com sua Adobe ID. Esse método entende que sua empresa foi provisionada na Experience Cloud e que você vinculou sua conta do Analytics. Para obter mais informações, consulte [Gerenciar usuários e produtos da Experience Cloud](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>Se não tiver certeza se sua empresa foi provisionada na Experience Cloud, use sua conta existente do Adobe Analytics.

### Adobe Analytics

Clique em **[!UICONTROL Fazer logon com o Analytics]** e digite o nome da empresa do Analytics, o nome de usuário e a senha.

## Criar um novo conjunto de relatórios {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Para criar um conjunto de relatórios para coletar dados do aplicativo e definir um aplicativo:

1. Clique em **[!UICONTROL Criar novo aplicativo]**.

   If you do not see this button, click **[!UICONTROL Manage Apps]** &gt; **[!UICONTROL Add]**.

1. No menu suspenso **[!UICONTROL Conjunto de relatórios]**, selecione **[!UICONTROL Novo conjunto de relatórios]**.

1. Digite o nome do aplicativo e selecione um tipo de conjunto de relatórios.

   Um exemplo de uma ID de conjunto de relatórios é `mycomobileappdev`. É necessário definir conjuntos de relatórios e aplicativos separados das versões de desenvolvimento e produção, de forma que possa repetir essas etapas quando estiver pronto para configurar a versão de produção.
1. In **[!UICONTROL Report Suite ID]**, verify that your report suite name is displayed.
1. Em **[!UICONTROL Copiar configurações de]**, verifique se **Modelo de aplicativo móvel]está selecionado.[!UICONTROL **

   Este modelo permite que os carimbos de data e hora coletem dados offline e ativem as variáveis da solução móvel para capturar medições de ciclo de vida.

1. Selecione o fuso horário, a moeda e clique em **[!UICONTROL Salvar]**.

## Baixar o SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Para baixar o SDK móvel:

1. Faça logon na interface do usuário do Mobile Services e abra o aplicativo de uma das seguintes maneiras:

   * Na lista suspensa **[!UICONTROL Todos os aplicativos], selecione o aplicativo.**
   * No painel direito, encontre seu aplicativo e abra-o.

1. Clique em **[!UICONTROL Gerenciar configurações do aplicativo]**.
1. Role até a seção **[!UICONTROL Downloads do SDK para aplicativos].**
1. Baixe o SDK e do aplicativo de exemplo para a sua plataforma.

>[!TIP]
>
>Um arquivo de configuração para seu aplicativo é incluído automaticamente no download do SDK, de modo que você não precisa baixar esse arquivo separadamente. No entanto, se já tiver baixado o SDK e deseja obter configurações atualizadas, baixe o arquivo de configuração novamente.

Se você usa o Android Studio, também é possível adicionar o seguinte código ao arquivo `build.gradle` do seu aplicativo.

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

Lembre-se das seguintes informações:

* Substitua o número da versão na amostra de código pela versão apropriada dos Android SDKs.
* Baixe o arquivo de configuração e inclua-o em seu projeto.