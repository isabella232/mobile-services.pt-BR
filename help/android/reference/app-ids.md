---
description: A tabela a seguir descreve os diferentes identificadores de aplicativos usados pelo Android SDK e pelo Adobe Mobile Services.
solution: Experience Cloud Services,Analytics
title: IDs da Apple
topic-fix: Developer and implementation
uuid: 3ac99489-6269-439e-a814-24102ef220b1
exl-id: 28358dd6-50dd-4ba9-9fb0-5271eae69d28
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 100%

---

# IDs da Apple{#app-ids}

A tabela a seguir descreve os diferentes identificadores de aplicativos usados pelo Android SDK e pelo Adobe Mobile Services.

| ID | Descrição |
|--- |--- |
| ID enviada com métricas de ciclo de vida | Esta é uma combinação do nome do aplicativo e da versão do pacote que é enviada para a loja de aplicativos. Este valor é usado para o relatório de Versões no Adobe Mobile Services; é possível filtrar usando esse valor para segmentar por uma versão específica do aplicativo. |
| ID da App Store | Essa ID é atribuída ao seu aplicativo pela loja de aplicativos e é fornecida no Adobe Mobile Services quando você cria links de aquisição. |
| AppID na Configuração JSON do ADBMobile | Este é um identificador exclusivo atribuído à instância do aplicativo pelo Adobe Mobile Services para todos os metadados associados no sistema. Essa ID é usada para criar URLs únicos para rastreamento de aquisição ou link de rastreamento. A ID é adicionada automaticamente ao arquivo de configuração JSON do ADBMobile quando for baixado da interface do usuário e pode ser encontrada em Gerenciar configurações do aplicativo nas configurações de Aquisição do aplicativo. |
