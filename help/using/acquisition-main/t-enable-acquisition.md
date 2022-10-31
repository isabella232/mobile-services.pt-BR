---
description: Para rastrear e criar relatórios sobre os links de marketing, é necessário ativar o rastreamento de aquisições na configuração do SDK.
keywords: dispositivos móveis
solution: Experience Cloud Services,Analytics
title: Configurar aquisição
topic-fix: Metrics
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
exl-id: 3a12dfab-70d0-41e6-8d4e-5aba21bb8606
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 100%

---

# Configurar aquisição {#configure-acquisition}

{#eol}

Para rastrear e criar relatórios sobre os links de marketing, é necessário ativar o rastreamento de aquisições na configuração do SDK.

1. Na página Gerencia configurações do aplicativo do aplicativo, navegue até a seção **[!UICONTROL Opções de aquisição do SDK.]**
1. Conclua as seguintes tarefas:

   * Para ativar a Aquisição, marque a caixa de seleção **[!UICONTROL Ativar]**.

      Ao marcar esta caixa de seleção, o campo **[!UICONTROL Tempo limite do referenciador]** fica ativo e o valor muda de 0 para 5.

   * Insira um valor no campo **[!UICONTROL Tempo limite do referenciador (segundos)]**

      (**Opcional**) Se você ativou a caixa de seleção **[!UICONTROL Ativar]**, esse campo é opcional. Você pode alterar o valor do tempo limite, que é especificado em segundos. Esta configuração especifica o tempo de espera pelas informações de aquisição antes de enviar a ocorrência da Primeira inicialização.
   >[!IMPORTANT]
   >Você deve inserir um valor diferente de zero. Se você habilitar a Aquisição, mas deixar o valor igual a zero, os links de Aquisição não funcionarão. Recomendamos usar o valor padrão de 5 segundos.

1. Baixe e use o novo arquivo de configuração do SDK em seu aplicativo.

   O Acquisition foi configurado com sucesso no **iOS**.
