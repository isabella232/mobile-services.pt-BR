---
description: Você pode configurar as opções do Analytics do SDK na página Gerenciar configurações do aplicativo, enquanto cria um novo aplicativo ou edita um aplicativo existente.
keywords: mobile
seo-description: Você pode configurar as opções do Analytics do SDK na página Gerenciar configurações do aplicativo, enquanto cria um novo aplicativo ou edita um aplicativo existente.
seo-title: Configuração de opções de SDK do Analytics
solution: Experience Cloud,Analytics
title: Configuração de opções de SDK do Analytics
topic: Metrics
uuid: fd3a21d2-6560-4e96-92fe-b99caac5e834
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 65%

---


# Configurar as opções do Analytics do SDK {#configure-sdk-analytics-options}

Você pode configurar as opções do Analytics do SDK na página Gerenciar configurações do aplicativo, enquanto cria um novo aplicativo ou edita um aplicativo existente.

Digite as informações nos seguintes campos em **[!UICONTROL Opções do Analytics do SDK]**:

* **[!UICONTROL Usar HTTPS]**

   Ative o HTTPS para ter mais segurança.

* **[!UICONTROL Colocar data retroativa em hits da sessão]**

   Ative/desative a capacidade do Adobe SDK de colocar data retroativa nas ocorrências de informação da sessão. Atualmente, as ocorrências de informação da sessão são os travamentos e a duração da sessão. Quando ativado, o SDK do Adobe retrodatará a ocorrência de informações da sessão para 1 segundo após a última ocorrência da sessão anterior. Isso significa que os dados de falhas e de sessão estarão relacionados à data correta em que ocorreram. Uma ocorrência receberá data retroativa em cada nova inicialização do aplicativo. Quando desativado, o Adobe SDK anexará as informações da sessão ao ciclo de vida atual.

* **[!UICONTROL Privacidade]**

   Selecione uma opção de privacidade:

   * **[!UICONTROL Enviar dados até a não participação]**
   * **[!UICONTROL Manter dados até a aceitação]**

* **[!UICONTROL Tempo limite da sessão (segundos)]**

   Especifique o valor do tempo limite da sessão.

   O limite padrão é de 300 segundos. Especifica a duração, em segundos, entre as inicializações do aplicativo antes que a inicialização seja considerada uma nova sessão. Esse tempo limite também se aplica quando o aplicativo é enviado para o plano de fundo e reativado. O tempo que o aplicativo gasta em segundo plano não é incluído na duração da sessão.

* **[!UICONTROL Limite do lote]**

   Especifique quantos hits deseja colocar na fila antes de enviar os dados.

   Defina como 0 para enviar os hits imediatamente. O limite de lote representa o limite para o número de ocorrências a serem enviadas em chamadas consecutivas. Por exemplo, se essa opção estiver definida como 10, cada ocorrência anterior à 10ª ocorrência será armazenada na fila. Quando a 10ª ocorrência entrar, todas as 10 ocorrências são enviadas consecutivamente.

* **[!UICONTROL Mais detalhes]**

   Clique no link **[!UICONTROL Mais detalhes]** para exibir a ID do conjunto de relatórios e o servidor de rastreamento, ativar ou desativar o rastreamento offline e exibir o modelo de codificação de caracteres em uso (como UTF-8).

   Quando o rastreamento offline é ativado, os dados gerados pelo dispositivo enquanto offline são marcados com carimbo de data e hora e enviados posteriormente. Se essa opção estiver desativada, os dados offline serão descartados.
