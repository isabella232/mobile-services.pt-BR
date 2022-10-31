---
description: No Adobe Analytics, é possível gerenciar as funções na página inicial das Ferramentas administrativas.
title: Funções e permissões
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 46%

---

# Funções e permissões{#roles-and-permissions}

{#eol}

No Adobe Analytics, é possível gerenciar as funções na página inicial das Ferramentas administrativas.

## Visão geral {#section_91B8192891E14E5285718C8118912500}

As seguintes funções gerenciam permissões na interface do usuário do Mobile Services:

### Administrador do Analytics

Um Administrador do Analytics gerencia grupos de usuários e atribui permissões, um deles é o Administrador do aplicativo móvel. O Experience Cloud Admin vincula sua Adobe ID à sua conta da Adobe Analytics, o que permite fazer logon na interface do usuário do Mobile Services usando sua Adobe ID. Para obter mais informações sobre o Administrador do Experience Cloud, consulte [Gerenciar usuários e produtos do Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=pt-BR) no guia Componentes da interface central do Experience Cloud.

>[!TIP]
>
>Um administrador existente do Analytics pode atribuir a função de administrador do Analytics a qualquer usuário.

### Administrador de aplicativos para dispositivos móveis

Esta é a função de administrador da interface do usuário do Mobile Services.

>[!IMPORTANT]
>
>Para alguns recursos, como mensagens por push, o administrador do Analytics deve marcar a caixa de seleção **[!UICONTROL Criação de segmentos]**, no Gerenciamento de usuários.

## Gerenciamento do acesso {#section_E6939C2695AA4A0DBF432D50B2670920}

Estas são algumas informações adicionais sobre como acessar opções na interface do usuário do Mobile Services:

### Aplicativos e conjuntos de relatórios

Todos os aplicativos do Mobile Service são vinculados aos conjuntos de relatórios. Se os usuários não tiverem acesso a um conjunto de relatórios, eles não terão acesso ao aplicativo associado desse conjunto de relatórios.

### Recursos do Mobile Services e do Analytics

Se a empresa não tiver um contrato do Analytics para acessar um recurso na interface do usuário, como as Mensagens de push, nenhum usuário da sua empresa terá acesso a esse recurso, independentemente do nível de permissão.

## Funções e permissões {#section_20AA029D5B8C413C8659777E79B11620}

Estas são as funções na interface do usuário do Mobile Services, com suas permissões relevantes:

### Administrador do Analytics permissões

* Todas as permissões de usuário e administrador de aplicativos móveis
* Criar aplicativo com o novo conjunto de relatórios
* Excluir aplicativo do Mobile Services

   >[!IMPORTANT]
   >
   >Embora o aplicativo tenha sido excluído da interface do Mobile Services, o conjunto de relatórios ainda existe no Analytics.

* Gerenciar configurações do aplicativo

   * Ativar relatórios de ciclo de vida
   * Ativar relatório de localização
   * Criar/atualizar/excluir variáveis e métricas

### Administrador de aplicativos para dispositivos móveis permissões

* Todas as permissões do usuário
* Criar aplicativo com o conjunto de relatórios existente
* Gerenciar configurações do aplicativo

   * Configurar as opções do SDK móvel do aplicativo
   * Definir as configurações da interface do usuário do aplicativo
   * Configurar aplicativos vinculados do App Store
   * Configurar as opções do Link universal do aplicativo
   * Configurar os certificados dos serviços de push e as chaves de API
   * Criar/atualizar/ativar/desativar/duplicar/arquivar/excluir postbacks
   * Criar/atualizar/arquivar/excluir destinos de links

* Criar/atualizar/arquivar links de marketing
* Criar/importar/atualizar/excluir links de aquisição herdada
* Criar/importar/atualizar/excluir configurações de locais (Pontos de interesse)
* Criar/atualizar/enviar/agendar/cancelar/duplicar/arquivar/excluir mensagens de push
* Criar/atualizar/ativar/desativar/duplicar/arquivar/excluir mensagens no aplicativo

Para obter mais informações sobre grupos e usuários, consulte o seguinte conteúdo na documentação do Adobe Analytics:

* [Configurações de grupo de usuários (herdado)](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=pt-BR)
* [Adicionar usuário a um grupo](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Usuário do Mobile Services

Essa função tem permissões somente visualização e pode fornecer feedback na interface do usuário do Mobile Services.

* Fornecer feedback sobre a interface do usuário do Mobile Services
* Exibir aplicativos

   >[!IMPORTANT]
   >
   >Os usuários só podem ver os conjuntos de relatórios para os quais têm acesso no Adobe Analytics.

* Exibir configurações do aplicativo

   * Baixar a configuração do SDK do aplicativo
   * Exibir todas as configurações da interface do usuário e do SDK
   * Exibir a configuração de variáveis e métricas
   * Exibir postbacks
   * Exibir destinos de links

* Exibir e executar relatórios
* Exibir links de marketing
* Exibir e exportar links de aquisição herdada
* Exibir e exportar a configuração de locais (pontos de interesse)
* Exibir mensagens de push
* Exibir mensagens no aplicativo
