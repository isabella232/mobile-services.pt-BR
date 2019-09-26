---
description: No Adobe Analytics, é possível gerenciar as funções na página inicial das Ferramentas administrativas.
seo-description: No Adobe Analytics, é possível gerenciar as funções na página inicial das Ferramentas administrativas.
seo-title: Funções e permissões
title: Funções e permissões
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
translation-type: tm+mt
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98

---


# Roles and permissions{#roles-and-permissions}

No Adobe Analytics, é possível gerenciar as funções na página inicial das Ferramentas administrativas.

## Visão geral {#section_91B8192891E14E5285718C8118912500}

As seguintes funções gerenciam permissões na interface do usuário do Mobile Services:

### Administrador do Analytics

Um administrador do Analytics gerencia grupos de usuários e atribui permissões, um deles é o administrador do Aplicativo móvel. O administrador da Experience Cloud vincula sua Adobe ID à conta do Adobe Analytics, o que permite fazer logon na interface do usuário do Mobile Services com o uso da Adobe ID. Para obter mais informações sobre o Administrador da Experience Cloud, consulte [Administração - Gerenciamento de usuários e perguntas frequentes](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>Um administrador existente do Analytics pode atribuir a função de administrador do Analytics a qualquer usuário.

Para obter mais informações sobre essa função, consulte o seguinte conteúdo:

* [User management overview](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/users.html)

* [Alterações de permissão de usuário e grupo](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/permissions-changes.html)

### Administrador de aplicativos para dispositivos móveis

Esta é a função de administrador da interface do usuário do Mobile Services.

>[!IMPORTANT]
>
>For some features, such as push messaging, the Analytics Admin must select the **[!UICONTROL Segment Creation]** check box in User Management.

## Managing access {#section_E6939C2695AA4A0DBF432D50B2670920}

Estas são algumas informações adicionais sobre como acessar opções na interface do usuário do Mobile Services:

### Apps and report suites

Todos os aplicativos do Mobile Service estão vinculados aos conjuntos de relatórios. Se os usuários não tiverem acesso a um conjunto de relatórios, eles não terão acesso ao seu aplicativo associado.

### Recursos do Mobile Services e do Analytics

Se a empresa não tiver um contrato do Analytics para acessar um recurso na interface do usuário, como as Mensagens de push, nenhum usuário da sua empresa terá acesso a esse recurso, independentemente do nível de permissão.

## Roles and permissions {#section_20AA029D5B8C413C8659777E79B11620}

Estas são as funções na interface do usuário do Mobile Services, com suas permissões relevantes:

### Administrador do Analytics

* Todas as permissões de usuário e administrador do aplicativo móvel
* Criar aplicativo com um novo conjunto de relatórios
* Excluir aplicativo do Mobile Services

   >[!IMPORTANT]
   >
   >Embora o aplicativo tenha sido excluído na interface do usuário do Mobile Services, o conjunto de relatórios ainda existe no Analytics.

* Gerenciar configurações do aplicativo

   * Ativar relatórios de ciclo de vida
   * Ativar relatórios de localização
   * Variáveis e métricas Criar/Atualizar/Excluir

### Administrador de aplicativos para dispositivos móveis

* Todas as permissões do usuário
* Criar aplicativo com o conjunto de relatórios existente
* Gerenciar configurações do aplicativo

   * Configurar as opções do SDK móvel do aplicativo
   * Configurar a interface do usuário do aplicativo
   * Configurar aplicativos vinculados da App Store
   * Configurar as opções de links universais do aplicativo
   * Configurar os certificados dos serviços de push e as chaves de API
   * Criar/atualizar/ativar/desativar/duplicar/arquivar/excluir postbacks
   * Criar/atualizar/arquivar/excluir destinos de links

* Criar/atualizar/arquivar links de marketing
* Criar/importar/atualizar/excluir links herdados de aquisição
* Criar/importar/atualizar/excluir configurações de locais (Pontos de interesse)
* Criar/atualizar/enviar/agendar/cancelar/duplicar/arquivar/excluir mensagens de push
* Criar/atualizar/ativar/desativar/duplicar/arquivar/excluir mensagens no aplicativo

Para obter mais informações sobre grupos e usuários, consulte:

* [User group settings](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-groups/groups.html)
* [Adicionar usuário a um grupo](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Usuário do Mobile Services

Esta função tem permissões somente exibição e pode fornecer feedback na interface do usuário do Mobile Services.

* Fornecer feedback sobre a interface do usuário do Mobile Services
* Exibir aplicativos

   >[!IMPORTANT]
   >
   >Os usuários podem ver apenas os conjuntos de relatórios aos quais têm acesso no Adobe Analytics.

* Exibir configurações do aplicativo

   * Baixar a configuração do SDK do aplicativo
   * Exibir todas as configurações de interface do usuário e SDK
   * Exibir a configuração de variáveis e métricas
   * Exibir postbacks
   * Exibir destinos de links

* View and Run Reports
* Exibir links de marketing
* Exibir e exportar links de aquisição herdados
* Exibir e exportar a configuração de locais (Pontos de interesse)
* Exibir mensagens de push
* Exibir mensagens no aplicativo
