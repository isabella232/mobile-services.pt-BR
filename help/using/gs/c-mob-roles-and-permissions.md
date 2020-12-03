---
description: No Adobe Analytics, é possível gerenciar as funções na página inicial das Ferramentas administrativas.
seo-description: No Adobe Analytics, é possível gerenciar as funções na página inicial das Ferramentas administrativas.
seo-title: Funções e permissões
title: Funções e permissões
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
translation-type: tm+mt
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 56%

---


# Funções e permissões{#roles-and-permissions}

No Adobe Analytics, é possível gerenciar as funções na página inicial das Ferramentas administrativas.

## Visão geral {#section_91B8192891E14E5285718C8118912500}

As seguintes funções gerenciam permissões na interface do usuário do Mobile Services:

### Administrador do Analytics

Um administrador do Analytics gerencia grupos de usuários e atribui permissões, uma das quais é o administrador do aplicativo móvel. O administrador do Experience Cloud vincula seu Adobe ID à sua conta do Adobe Analytics, o que permite fazer logon na interface do usuário do Mobile Services usando seu Adobe ID. Para obter mais informações sobre o Administrador da Experience Cloud, consulte [Administração - Gerenciamento de usuários e perguntas frequentes](https://docs.adobe.com/content/help/pt-BR/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>Um administrador existente do Analytics pode atribuir a função de administrador do Analytics a qualquer usuário.

Para obter mais informações sobre essa função, consulte o seguinte conteúdo:

* [Visão geral do gerenciamento de usuários](https://docs.adobe.com/content/help/pt-BR/analytics/admin/user-product-management/user-management/users.html)

* [Mudanças nas permissões de usuários e grupos](https://docs.adobe.com/content/help/pt-BR/analytics/admin/user-product-management/user-management/permissions-changes.html)

### Administrador de aplicativos para dispositivos móveis

Esta é a função de administrador da interface do usuário do Mobile Services.

>[!IMPORTANT]
>
>Para alguns recursos, como mensagens por push, o administrador do Analytics deve marcar a caixa de seleção **[!UICONTROL Criação de segmentos]**, no Gerenciamento de usuários.

## Gerenciamento do acesso {#section_E6939C2695AA4A0DBF432D50B2670920}

Estas são algumas informações adicionais sobre como acessar opções na interface do usuário do Mobile Services:

### Aplicativos e conjuntos de relatórios

Todos os aplicativos do Mobile Service estão vinculados aos conjuntos de relatórios. Se os usuários não tiverem acesso a um conjunto de relatórios, eles não terão acesso ao aplicativo associado do conjunto de relatórios.

### Recursos do Mobile Services e do Analytics

Se a empresa não tiver um contrato do Analytics para acessar um recurso na interface do usuário, como as Mensagens de push, nenhum usuário da sua empresa terá acesso a esse recurso, independentemente do nível de permissão.

## Funções e permissões{#section_20AA029D5B8C413C8659777E79B11620}

Estas são as funções na interface do usuário do Mobile Services, com suas permissões relevantes:

### Administrador do Analytics

* Todas as permissões de usuário e administrador de aplicativos móveis
* Criar aplicativo com novo conjunto de relatórios
* Excluir aplicativo do Mobile Services

   >[!IMPORTANT]
   >
   >Embora o aplicativo tenha sido excluído da interface do Mobile Services, o conjunto de relatórios ainda existe no Analytics.

* Gerenciar configurações do aplicativo

   * Ativar o Relatórios do ciclo de vida
   * Ativar Relatórios de localização
   * Criar/atualizar/excluir variáveis e métricas

### Administrador de aplicativos para dispositivos móveis

* Todas as permissões do usuário
* Criar aplicativo com conjunto de relatórios existente
* Gerenciar configurações do aplicativo

   * Configurar as opções do SDK móvel do aplicativo
   * Definir configurações da interface do usuário do aplicativo
   * Configurar aplicativos vinculados da App Store
   * Configurar as opções de Link universal do aplicativo
   * Configurar certificados de serviços de push e chaves de API
   * Criar/atualizar/ativar/desativar/Duplicado/arquivar/excluir postbacks
   * Criar/atualizar/arquivar/excluir destinos de links

* Criar/atualizar/arquivar links de marketing
* Criar/importar/atualizar/excluir links de aquisição herdados
* Configuração Criar/Importar/Atualizar/Excluir locais (Pontos de interesse)
* Criar/atualizar/enviar/agendar/cancelar/Duplicado/arquivar/excluir mensagens de push
* Criar/atualizar/ativar/desativar/Duplicado/arquivar/excluir mensagens no aplicativo

Para obter mais informações sobre grupos e usuários, consulte:

* [Configurações do grupo de usuários](https://docs.adobe.com/content/help/pt-BR/analytics/admin/user-product-management/user-groups/groups.html)
* [Adicionar usuário a um grupo](https://docs.adobe.com/content/help/pt-BR/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Usuário do Mobile Services

Essa função tem permissões somente para visualizações e pode fornecer feedback na interface do usuário do Mobile Services.

* Fornecer feedback sobre a interface do usuário do Mobile Services
* Aplicativos de visualização

   >[!IMPORTANT]
   >
   >Os usuários só podem ver os conjuntos de relatórios para os quais têm acesso no Adobe Analytics.

* Configurações do aplicativo de visualização

   * Download da configuração do SDK do aplicativo
   * Visualização de todas as configurações da interface do usuário e do SDK
   * Configuração de variáveis e métricas de visualização
   * Postbacks de visualização
   * Destinos do link de visualização

* Exibir e executar relatórios
* Exibir links de marketing
* Visualização e exportação de links de aquisição herdados
* Configuração de locais de visualização e exportação (pontos de interesse)
* Mensagens de push de visualização
* Mensagens no aplicativo da visualização
