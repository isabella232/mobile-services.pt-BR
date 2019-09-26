---
description: Você pode configurar as opções de público-alvo para mensagens no aplicativo, incluindo as opções de exibição, acionador e característica.
keywords: mobile
seo-description: Você pode configurar as opções de público-alvo para mensagens no aplicativo, incluindo as opções de exibição, acionador e característica.
seo-title: Mensagem no aplicativo do público-alvo
solution: Marketing Cloud,Analytics
title: Mensagem no aplicativo do público-alvo
topic: Métricas
uuid: 6c815d4c-7626-4cf4-9158-3f059c79317a
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Audience: in-app message {#audience-in-app-message}

Você pode configurar as opções de público-alvo para mensagens no aplicativo, incluindo as opções de exibição, acionador e característica.

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. Na página Público-alvo, digite as informações nos seguintes campos:

   * **[!UICONTROL Exibir]**

      Selecione a opção que aciona uma mensagem para exibir:

      * **[!UICONTROL Sempre]**

         Esta opção significa que a mensagem é exibida sempre que o acionamento ocorre.

      * **[!UICONTROL Uma vez]**

         Esta opção significa que a mensagem é exibida somente na primeira vez que o acionamento ocorre.

      * **[!UICONTROL Até o click-through]**

         Esta opção significa que a mensagem é exibida sempre que o acionamento ocorre até o click-through. Esse acionamento aplica-se somente a mensagens de alerta e em tela cheia. A maioria das mensagens precisam ser redirecionadas ou usar um recurso da internet e não serão exibidas se estiver offline. Para mostrar a mensagem sempre, independentemente da conectividade de rede, marque a caixa de seleção **[!UICONTROL Exibir offline].**
   * **[!UICONTROL Acionador]**

      Selecione uma opção na lista suspensa e escolha uma condição. Por exemplo, você poderia escolher **[!UICONTROL Lançado]** na lista suspensa e **Existe]na segunda lista suspensa.[!UICONTROL ** Você também pode especificar dados de contexto personalizados, que precisam estar na ocorrência do acionamento para exibir a mensagem.

      >[!IMPORTANT]
      >
      >Se você selecionar vários acionadores para que a mensagem seja exibida, todos devem ocorrer na mesma ocorrência.

   * **[!UICONTROL Características]** Você pode determinar quem deve ver a mensagem no aplicativo quando ela é acionada e filtrar (segmentar) o público-alvo para ocorrências que tenham dados especificados. Por exemplo, é possível definir uma regra segundo a qual os Pontos de interesse contenham Denver. Este filtro permite mostrar a mensagem aos clientes que estão em um dos seus pontos de interesse com Denver no nome, no momento do acionamento.



## Additional information about traits and triggers {#section_48C39EFB8CAA4F62B994FCC91DF588E6}

>[!IMPORTANT]
>
>Acionadores e características usam dados que são passados para o Analytics a partir do seu aplicativo. Esses valores são transmitidos como dados de contexto, variáveis mapeadas e métricas. Uma variável é um valor com base em texto, e uma métrica é um valor numérico.

To see the mapping of these key value pairs in the Mobile Services UI and validate the value for your trigger, click **[!UICONTROL Manage App Settings]** &gt;  **[!UICONTROL Manage Variables &amp; Metrics]** &gt;, which displays the following tabs:

* **[!UICONTROL Variáveis e métricas padrão]**
* **[!UICONTROL Variáveis personalizadas]**
* **[!UICONTROL Métricas personalizadas]**

Depois de validar o mapeamento, selecione a correspondência ou operador lógico adequado para configurar o público-alvo da mensagem.

### Selecting metrics and variables {#example_AB126F03BD1C4094B791E230B3DB1189}

![trigger options](assets/custom_trigger_matcher_options.png)

Os seguintes cenários ajudam a determinar se uma métrica ou variável deve ser selecionada como seu acionador:

### Métricas

Uma métrica é um número, e um exemplo é o número de compras.

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. Complete as etapas na seção **[!UICONTROL Acionador]** da guia **Público-alvo[!UICONTROL :]**

   1. Selecione um evento padrão como **[!UICONTROL Iniciado]** e, em seguida **[!UICONTROL existe]**.
   1. Selecione um segundo acionador que seja um ponto de dados personalizado mapeado a uma métrica.
   1. Under **[!UICONTROL Number]**, select a matcher option.

### Variáveis

Uma variável é uma cadeia de caracteres de texto que é um identificador único, como país e aeroporto, por exemplo.

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. Complete as etapas na seção **[!UICONTROL Acionador]** da guia **Público-alvo[!UICONTROL :]**

   1. Selecione um evento padrão como **[!UICONTROL Iniciado]** e, em seguida **[!UICONTROL existe]**.
   1. Selecione um segundo acionador que seja um ponto de dados personalizado mapeado a uma variável.
   1. Under **[!UICONTROL Text]**, select a matcher option.

For more information about context data, variables, and metrics, see [Managing your app](/help/using/manage-apps/manage-apps.md).
