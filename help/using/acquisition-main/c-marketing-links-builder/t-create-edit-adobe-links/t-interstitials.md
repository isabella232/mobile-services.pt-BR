---
description: É possível direcionar os usuários para um destino, dependendo se eles têm o aplicativo instalado (um deep link de aplicativo) ou não (para um site ou uma app store).
keywords: mobile
seo-description: É possível direcionar os usuários para um destino, dependendo se eles têm o aplicativo instalado (um deep link de aplicativo) ou não (para um site ou uma app store).
seo-title: Intersticiais
solution: Marketing Cloud,Analytics
title: Intersticiais
topic: Métricas
uuid: 7dce8ab2-2a5d-4384-ac1e-e31dfaa33654
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Intersticiais{#interstitials}

É possível direcionar os usuários para um destino, dependendo se eles têm o aplicativo instalado (um deep link de aplicativo) ou não (para um site ou uma app store). É melhor deixar a escolha do roteamento para os usuários. Os profissionais de marketing podem fornecer opções aos usuários, configurando uma página intersticial que mostra aos usuários os destinos disponíveis.

Para configurar um intersticial ao criação de um Link de marketing:

1. Click **[!UICONTROL Edit Deep Link Interstitial]**.

   ![Deep link interstitial](assets/interstitial2.png)

1. Digite informações nos seguintes campos:

   * **[!UICONTROL HTML personalizado]**

      Selecione sua página HTML intersticial personalizada.

      Ao usar intersticiais personalizados, os profissionais de marketing podem personalizar páginas de aterrissagem intersticiais com HTML/CSS/JS personalizados, o que permite que você atribua uma marca às suas páginas.

      Estes são os requisitos da página HTML:

      * Deve ser um arquivo HTML.
      * Must contain the `%%DEST%%` and `%%FALLBACK%%` placeholders.
      * O HTML carregado será tratado em um `<iframe>`.

         Você deve garantir que os destinos dos links apontem para uma janela principal. You can include `<base target="_parent" />` in `<head>` or specify a target property for each `<a/>` individually.

         >[!TIP]
         >
         >Se você carregar HTML personalizado, as outras quatro opções nesta tabela não serão usadas a menos que você remova o arquivo carregado.
   * **[!UICONTROL URL da imagem]**

      Especifique o URL para um ativo de imagem.

   * **[!UICONTROL Corpo de texto]**

      Especifique o texto do corpo para o intersticial.

   * **[!UICONTROL Texto de confirmação]**

      Especifique o texto para o botão de texto.

   * **[!UICONTROL Texto de fallback]**

      Especifique o texto de fallback para exibir.

      Este campo atualizará o botão de texto se um deep link falhar. Os usuários são direcionados para experimentar o deep link para que possam voltar para outra opção. Por exemplo, uma emergência pode ser para uma app store para baixar e instalar o aplicativo ou levar os usuários para o site da empresa. O texto de fallback permite que os usuários saibam que há outra opção disponível se ocorrer uma falha no link direto.


1. (**Optional**) Click the icons above the image to see how the interstitial looks rotated and on different devices.

   Você pode alterar ou editar a imagem fora do Mobile Services para garantir que a imagem seja exibida corretamente em diferentes situações.
1. Clique em **[!UICONTROL Salvar]**.
