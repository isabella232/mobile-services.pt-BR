---
description: Você pode configurar as opções do Analytics do SDK na página Gerenciar configurações do aplicativo, enquanto cria um novo aplicativo ou edita um aplicativo existente.
keywords: mobile
seo-description: Você pode configurar as opções do Analytics do SDK na página Gerenciar configurações do aplicativo, enquanto cria um novo aplicativo ou edita um aplicativo existente.
seo-title: Configuração de opções de SDK do Analytics
solution: Marketing Cloud,Analytics
title: Configuração de opções de SDK do Analytics
topic: Métricas
uuid: fd3a21d2-6560-4e96-92fe-b99caac5e834
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configure SDK Analytics options {#configure-sdk-analytics-options}

Você pode configurar as opções do Analytics do SDK na página Gerenciar configurações do aplicativo, enquanto cria um novo aplicativo ou edita um aplicativo existente.

Type information in the following fields under **[!UICONTROL SDK Analytics Options]**:

* **[!UICONTROL Usar HTTPS]**

   Ativa o HTTPS para ter mais segurança.

* **[!UICONTROL Colocar data retroativa em hits da sessão]**

   Ative ou desative a capacidade do Adobe SDK de pré-datar as ocorrências de informações da sessão. Atualmente, as ocorrências de informação da sessão são os travamentos e a duração da sessão. Quando ativado, o Adobe SDK colocará data retroativa em informações da sessão para 1 segundo após o último hit da sessão anterior. Isso significa que os dados dos travamentos e da sessão estarão relacionados à data exata em que ocorreram. Uma ocorrência receberá data retroativa em cada nova inicialização do aplicativo. Quando desativado, o Adobe SDK anexará as informações da sessão ao ciclo de vida atual.

* **[!UICONTROL Privacidade]**

   Selecione uma opção de privacidade:

   * **[!UICONTROL Enviar dados até a não participação]**
   * **[!UICONTROL Manter dados até a aceitação]**

* **[!UICONTROL Tempo limite da sessão (segundos)]**

   Especifique o valor do tempo limite da sessão.

   O limite padrão é de 300 segundos. Especifica a duração, em segundos, entre as inicializações do aplicativo antes que a inicialização seja considerada uma nova sessão. Esse tempo de espera também se aplica quando seu aplicativo é enviado para segundo plano e reativado. O tempo que seu aplicativo gasta em segundo plano não está incluído na duração da sessão.

* **[!UICONTROL Limite do lote]**

   Especifique quantos hits deseja colocar na fila antes de enviar os dados.

   Defina como 0 para enviar os hits imediatamente. O limite do lote representa o limite para o número de hits que serão enviados em chamadas consecutivas. Por exemplo, se essa opção estiver definida como 10, cada hit antes do 10° hit será armazenado na fila. Quando o 10° hit entrar, todos os 10 hits serão enviados na ordem.

* **[!UICONTROL Mais detalhes]**

   Clique no link **[!UICONTROL Mais detalhes]para exibir a ID do conjunto de relatórios e o servidor de rastreamento, ativar ou desativar o rastreamento offline e exibir o modelo de codificação de caracteres em uso (como UTF-8).**

   Quando o rastreamento offline está desativado, os dados gerados enquanto o dispositivo está offline recebem o carimbo de data/hora e são enviados posteriormente. Se essa opção estiver desativada, os dados offline são descartados.
