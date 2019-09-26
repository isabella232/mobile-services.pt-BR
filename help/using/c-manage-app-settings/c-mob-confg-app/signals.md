---
description: Os postbacks permitem enviar os dados coletados pelo Adobe Mobile a um servidor separado de terceiros. Ao usar os mesmos acionadores e características usados para exibir uma mensagem no aplicativo, é possível configurar o Mobile Services para enviar dados personalizados a um destino de terceiros.
seo-description: Os postbacks permitem enviar os dados coletados pelo Adobe Mobile a um servidor separado de terceiros. Ao usar os mesmos acionadores e características usados para exibir uma mensagem no aplicativo, é possível configurar o Mobile Services para enviar dados personalizados a um destino de terceiros.
seo-title: Configuração de postbacks
title: Configuração de postbacks
uuid: a026575c-057b-4868-b6c8-9514cbc32b4d
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configure postbacks {#configure-postbacks}

Os postbacks permitem enviar os dados coletados pelo Adobe Mobile a um servidor separado de terceiros. Ao usar os mesmos acionadores e características usados para exibir uma mensagem no aplicativo, é possível configurar o Mobile Services para enviar dados personalizados a um destino de terceiros.

>[!IMPORTANT]
>
>To use postbacks, you must install the 4.6 SDK or later. Para obter mais informações, consulte [Android - Postbacks](/help/android/analytics-main/postbacks/postbacks.md) ou [iOS - Postbacks](/help/ios/analytics-main/postback/postback.md).

1. Clique no nome do aplicativo desejado para ir para a página Gerenciar configurações do aplicativo e clique no link **Gerenciar postbacks** no canto superior direito.
1. Clique em **[!UICONTROL Criar postback]**.
1. Digite as seguintes informações nos campos:

   * **[!UICONTROL Tipo de postback]**

      Selecione **[!UICONTROL Personalizar]**. Os modelos serão disponibilizados no futuro.

   * **[!UICONTROL Nome]**

      Especifique um nome descritivo para o postback.

   * **[!UICONTROL URL]**

      Especifique um URL de ponto de extremidade válido (com parâmetros de consulta adequados, conforme necessário, para solicitações GET). Esse URL é obtido com a parte na qual você está enviando os dados (servidor de publicidade ou seu próprio terminal). Por exemplo `https://my.server.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`.

   * **[!UICONTROL Variável de contexto]**

      Realce as partes do URL e selecione a variável de contexto desejada na lista suspensa. You can also insert context variables into the URL, and the URL will replace all template variables with values from the hit.

   * **[!UICONTROL Adicionar corpo da publicação]**

      Especifique qualquer outro conteúdo do corpo da postagem, por exemplo, em uma solicitação de postagem. Se você especificar o texto do corpo da postagem, especifique o tipo de conteúdo para o corpo da postagem. Por exemplo, `application/json`.

   * **[!UICONTROL Tempo limite (em segundos)]**

      Especifique o tempo (em segundos) para aguardar o postback.

   * **[!UICONTROL Acionadores]**

      Especifique uma ou mais tags de data e condições que acionam o postback. For example, you might choose **[!UICONTROL Crashed]** as the trigger and **[!UICONTROL Exists]** as the condition to trigger the postback when the app crashes. Você também pode especificar quais métricas ativam o postback. For example, you can select **[!UICONTROL Device Name]** as the trigger, **[!UICONTROL Equals]**, and **[!UICONTROL iPhone 6 Plus]** as conditions to activate the postback when the app crashes on iPhone 6 Plus devices.

   * **[!UICONTROL Característica(s)]**
   Especifique quem pode ver a mensagem quando ela é acionada. Options include **[!UICONTROL Session Length**, **[!UICONTROL First Launch Date]**, and **[!UICONTROL App ID]**.

1. Clique em **[!UICONTROL Salvar]** para criar o postback e adicioná-lo à lista **Gerenciar postbacks[!UICONTROL .]**

   Para ativar o postback no futuro, siga um destes procedimentos:

   * Marque a caixa de seleção ao lado do postback na lista **[!UICONTROL Gerenciar postbacks]** e clique em **[!UICONTROL Ativar seleção]**.
   * Clique em **[!UICONTROL Salvar e ativar]para salvar suas alterações e ativar imediatamente o postback.**
