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

Um administrador do Analytics gerencia grupos de usuários e atribui permissões, sendo que um deles é o administrador do aplicativo móvel. O administrador do Experience Cloud vincula o Adobe ID à sua conta Adobe Analytics, o que permite fazer logon na interface do usuário do Mobile Services usando sua Adobe ID. Para obter mais informações sobre o Administrador de Experience Cloud, consulte [Gerenciar usuários e produtos do Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=pt-BR) no guia Componentes da interface central do Experience Cloud.

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

Todos os aplicativos do Mobile Services estão vinculados aos conjuntos de relatórios. Se os usuários não tiverem acesso a um conjunto de relatórios, eles não terão acesso ao aplicativo associado desse conjunto de relatórios.

### Recursos do Mobile Services e do Analytics

Se a empresa não tiver um contrato do Analytics para acessar um recurso na interface do usuário, como as Mensagens de push, nenhum usuário da sua empresa terá acesso a esse recurso, independentemente do nível de permissão.

## Funções e permissões {#section_20AA029D5B8C413C8659777E79B11620}

Estas são as funções na interface do usuário do Mobile Services, com suas permissões relevantes:

### Administrador do Analytics permissões

* Todas as permissões de usuário e administrador de aplicativos móveis
* Criar aplicativo com um novo conjunto de relatórios
* Excluir aplicativo do Mobile Services

   >[!IMPORTANT]
   >
   >Embora o aplicativo tenha sido excluído da interface do Mobile Services, o conjunto de relatórios ainda existe no Analytics.

* Gerenciar configurações do aplicativo

   * Habilitar Relatórios de Ciclo de Vida
   * Ativar relatório de localização
   * Criar/Atualizar/Excluir variáveis e métricas

### Administrador de aplicativos para dispositivos móveis permissões

* Todas as permissões do usuário
* Criar aplicativo com conjunto de relatórios existente
* Gerenciar configurações do aplicativo

   * Configurar as opções do SDK móvel do aplicativo
   * Definir as configurações da interface do usuário do aplicativo
   * Configurar aplicativos vinculados do App Store
   * Configurar as opções de Link universal do aplicativo
   * Configurar certificados e chaves de API dos serviços de push
   * Criar/Atualizar/Ativar/Desativar/Duplicar/Arquivar/Excluir postbacks
   * Criar/Atualizar/Arquivar/Excluir destinos de links

* Criar/Atualizar/Arquivar links de marketing
* Criar/Importar/Atualizar/Excluir links de aquisição herdada
* Criar/Importar/Atualizar/Excluir configuração de Locais (Pontos de interesse)
* Criar/Atualizar/Enviar/Programar/Cancelar/Duplicar/Arquivar/Excluir mensagens por push
* Criar/Atualizar/Ativar/Desativar/Duplicar/Arquivar/Excluir mensagens no aplicativo

Para obter mais informações sobre grupos e usuários, consulte o seguinte conteúdo na documentação do Adobe Analytics:

* [Configurações do grupo de usuários (herdado)](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=pt-BR)
* [Adicionar usuário a um grupo](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=pt-BR)

### Usuário do Mobile Services

Esta função tem permissões somente para visualização e pode fornecer feedback na interface do usuário do Mobile Services.

* Fornecer feedback sobre a interface do usuário do Mobile Services
* Exibir aplicativos

   >[!IMPORTANT]
   >
   >Os usuários só podem ver os conjuntos de relatórios para os quais têm acesso no Adobe Analytics.

* Exibir configurações do aplicativo

   * Baixar configuração do SDK do aplicativo
   * Exibir todas as configurações de interface do usuário e SDK
   * Exibir configuração de variáveis e métricas
   * Exibir postbacks
   * Exibir destinos do link

* Exibir e executar relatórios
* Exibir links de marketing
* Visualizar e exportar links de aquisição herdada
* Visualizar e exportar a configuração de Locais (Pontos de interesse)
* Exibir mensagens de push
* Exibir mensagens no aplicativo
