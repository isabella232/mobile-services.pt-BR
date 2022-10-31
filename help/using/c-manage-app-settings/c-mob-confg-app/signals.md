---
description: Os postbacks permitem enviar dados coletados pelo Adobe Mobile para um servidor de terceiros separado. Ao usar os mesmos acionadores e características que você usa para exibir uma mensagem no aplicativo, você pode configurar os Mobile Services para enviar dados personalizados a um destino de terceiros.
title: Configurar postbacks
uuid: a026575c-057b-4868-b6c8-9514cbc32b4d
exl-id: 99b27f16-303a-4853-bfdb-2066a53867bf
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 100%

---

# Configurar postbacks {#configure-postbacks}

{#eol}

Os postbacks permitem enviar dados coletados pelo Adobe Mobile para um servidor de terceiros separado. Ao usar os mesmos acionadores e características que você usa para exibir uma mensagem no aplicativo, você pode configurar os Mobile Services para enviar dados personalizados a um destino de terceiros.

>[!IMPORTANT]
>
>Para usar postbacks, você deve instalar o SDK 4.6 ou versão posterior.

1. Clique no nome do aplicativo desejado para ir para a página Gerenciar configurações do aplicativo e clique no link **[!UICONTROL Gerenciar postbacks]** no canto superior direito.
2. Clique em **[!UICONTROL Criar postback]**.
3. Digite as seguintes informações nos campos:

   * **[!UICONTROL Tipo de postback]**

      Selecione **[!UICONTROL Personalizar]**. Os modelos serão disponibilizados no futuro.

   * **[!UICONTROL Nome]**

      Especifique um nome descritivo para o postback.

   * **[!UICONTROL URL]**

      Especifique um URL válido de terminal (com parâmetros de consulta apropriados, conforme necessário para as solicitações GET). Esse URL é obtido com a parte na qual você está enviando os dados (servidor de publicidade ou seu próprio terminal). Por exemplo `https://example.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`.

   * **[!UICONTROL Variável de contexto]**

      Realce as partes do URL e selecione a variável de contexto desejada na lista suspensa. Você também pode inserir variáveis de contexto no URL, e o URL substituirá todas as variáveis de modelo por valores da ocorrência.

   * **[!UICONTROL Adicionar corpo da publicação]**

      Especifique qualquer outro conteúdo do corpo da postagem, por exemplo, em uma solicitação de postagem. Se você especificar o corpo de texto da publicação, especifique o tipo de conteúdo para o corpo da publicação. Por exemplo, `application/json`.

   * **[!UICONTROL Tempo limite (em segundos)]**

      Especifique o tempo (em segundos) para aguardar o postback.

   * **[!UICONTROL Acionadores]**

      Especifique uma ou mais tags de data e condições que acionam o postback. Por exemplo, você pode escolher **[!UICONTROL Falha]** como acionador e **[!UICONTROL Existe]** como condição para acionar o postback quando o aplicativo travar. Você também pode especificar quais métricas ativam o postback. Por exemplo, você pode selecionar **[!UICONTROL Nome do dispositivo]** como acionador e **[!UICONTROL Igual]** e **[!UICONTROL iPhone 6 Plus]** como condições para ativar o postback quando o aplicativo travar em dispositivos iPhone 6 Plus.

   * **[!UICONTROL Característica(s)]**
   Especifique quem pode ver a mensagem quando ela é acionada. As opções incluem **[!UICONTROL Duração da sessão]**, **[!UICONTROL Data da primeira inicialização]** e **[!UICONTROL ID do aplicativo]**.

4. Clique em **[!UICONTROL Salvar]** para criar o postback e adicioná-lo à lista **[!UICONTROL Gerenciar postbacks]**.

   Para ativar o postback no futuro, siga um destes procedimentos:

   * Marque a caixa de seleção ao lado do postback na lista **[!UICONTROL Gerenciar postbacks]** e clique em **[!UICONTROL Ativar seleção]**.
   * Clique em **[!UICONTROL Salvar e ativar]** para salvar suas alterações e ativar imediatamente o postback.
