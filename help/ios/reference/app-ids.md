---
description: A tabela a seguir descreve os diferentes identificadores de aplicativos usados pelo SDK do iOS e pelo Adobe Mobile Services.
solution: Experience Cloud Services,Analytics
title: IDs da Apple
topic-fix: Developer and implementation
uuid: 24ebc716-23c7-4ee8-8256-b534210367e0
exl-id: 82f0a097-b2eb-4313-8624-dd442e3da039
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 100%

---

# IDs da Apple {#app-ids}

A tabela a seguir descreve os diferentes identificadores de aplicativos usados pelo SDK do iOS e pelo Adobe Mobile Services.

| ID | Descrição |
|--- |--- |
| ID enviada com métricas de ciclo de vida | Esta é uma combinação do nome do aplicativo e da versão do pacote que é enviada para a loja de aplicativos.  Esse valor é usado para o relatório Versões nos Adobe Mobile Services e ele pode ser usado para filtrar os resultados por uma versão específica do seu aplicativo. |
| ID da App Store | Essa ID é atribuída ao seu aplicativo pela loja de aplicativos e é fornecida no Adobe Mobile Services quando você cria links de aquisição. |
| AppID na Configuração JSON do ADBMobile | Este identificador é exclusivo e é atribuído à instância do aplicativo pelos Adobe Mobile Services para todos os metadados associados em seu sistema.  Esta ID é usada para criar os URLs exclusivos para o rastreamento de aquisição ou o link de rastreamento, é adicionado automaticamente ao arquivo de configuração ADBMobile JSON quando baixado da interface do usuário e pode ser encontrado em Gerenciar configurações do aplicativo nas configurações de Aquisição do seu aplicativo. |
