---
description: O rastreamento de aquisição deve ser ativado na configuração do SDK para que você possa rastrear e criar relatórios sobre Links de publicidade.
keywords: mobile
seo-description: O rastreamento de aquisição deve ser ativado na configuração do SDK para que você possa rastrear e criar relatórios sobre Links de publicidade.
seo-title: Configurar aquisição
solution: Marketing Cloud, Analytics
title: Configurar aquisição
topic: Métricas
uuid: e 996 e 43 e -8 a 77-47 a 3-a 6-a 6 fb -53 f 676 f 92
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Configurar aquisição {#configure-acquisition}

O rastreamento de aquisição deve ser ativado na configuração do SDK para que você possa rastrear e criar relatórios sobre Links de publicidade.

1. Na página Gerencia configurações do aplicativo do aplicativo, navegue até a seção **[!UICONTROL Opções de aquisição do SDK.]**
1. Conclua as seguintes tarefas:

   * To enable Acquisition, select the **[!UICONTROL Enable]** check box.

      When you select this check box, the **[!UICONTROL Referrer Timeout]** field becomes active, and the value changes from 0 to 5.

   * Inserir um valor no campo Tempo limite **[!UICONTROL do referenciador (segundos)]**

      (**Opcional**) Se você ativou **[!UICONTROL a caixa]** de seleção Ativar, este campo é opcional. Você pode alterar o valor do tempo limite, que é especificado em segundos. Essa configuração especifica o período para aguardar as informações de Aquisição antes de enviar a ocorrência da Primeira inicialização.
   >[!IMPORTANT]
   >Você deve inserir um valor diferente de zero. Se você ativar a Aquisição, mas deixar o valor como zero, os links de Aquisição não funcionarão. Recomendamos que você use o valor padrão de 5 segundos.

1. Baixe e use o novo arquivo de configuração do SDK em seu aplicativo.

   O Acquisition foi configurado com sucesso no **iOS**.
To enable Acquisition on **Android**, complete the steps in [Tracking Mobile Acquisition](/help/android/acquisition-main/acquisition.md).
