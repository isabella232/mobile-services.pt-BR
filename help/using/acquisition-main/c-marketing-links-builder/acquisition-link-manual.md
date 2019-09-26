---
description: You can create Marketing Links to acquire new mobile app users on-the-fly by manually configuring the URL parameters.
keywords: mobile
seo-description: You can create Marketing Links to acquire new mobile app users on-the-fly by manually configuring the URL parameters.
seo-title: Criar links de aquisição manualmente
solution: Marketing Cloud,Analytics
title: Criar links de aquisição manualmente
topic: Métricas
uuid: d7709203-f793-4982-adaa-9c3c914aca2b
translation-type: tm+mt
source-git-commit: 54e3b2d673356a616987537d20758bef8b044db4

---


# Criar links de aquisição manualmente {#create-acquisition-link-manually}

Você pode criar Marketing Links para adquirir novos usuários de aplicativos móveis dinamicamente, configurando manualmente os parâmetros de URL.

>[!IMPORTANT]
>
>Este recurso exige a versão 4.6 ou posterior do SDK. Para obter mais informações, consulte Pré-requisitos [de aquisição](/help/using/acquisition-main/c-acquisition-prerequisites.md).

O diagrama a seguir ilustra os componentes de um link de rastreamento criado manualmente e exibe os diferentes parâmetros de URL que você deve configurar corretamente ao criar links de aquisição manualmente.

![](assets/acquisition_url.png)

Este link foi configurado para executar um redirecionamento específico da plataforma para a Google Play Store ou a Apple App Store em um aplicativo móvel. Se não for possível determinar o destino, a Apple App Store será definida como a loja padrão. Após a instalação do aplicativo, a chave de contexto personalizado `my.custom.key:test` é anexada à ocorrência de instalação do Analytics.

Para criar links manualmente, use o seguinte formato de URL:

`http(s)://c00.adobe.com/v3/ {mobile-services-app-hash}/start? {parameters}`

>[!TIP]
>
>A versão do Android SDK que você está usando não tem impacto neste processo.

Para o iOS, assegure-se de usar o protocolo correto:

* Use **HTTP** if you are using the iOS SDKs before version 4.7.0, or if you are using iOS SDK 4.7.0 or later, and if **[!UICONTROL Use HTTPS]** is **not** selected on the Manage App Settings page.
* Use **HTTPS** se estiver usando o SDK 4.7.0 ou posterior do iOS e **[!UICONTROL Usar HTTPS]****estará** selecionado na página Gerenciar configurações do aplicativo.

Quando as seguintes condições são cumpridas:

* `{mobile-services-app-hash}` corresponde ao identificador do aplicativo no arquivo de configuração `acquisition:appid ` .

   You can locate `{mobile-services-app-hash}` in the Manage App Settings page under Acquisition SDK Options in the Tracking ID field.

   ![](assets/tracking-id.png)

* `{parameters}` é uma lista de parâmetros de consulta de URL padrão com nomes específicos.

Esta é a lista de parâmetros:

* **`a_g_id`**

   Identificador de aplicativo do Google Play Store.

   * Valor da amostra: `com.adobe.beardcons`

* **`a_g_lo`**

   Substituição local do Google Play Store.

   * Valor da amostra: `ko`

* **`a_i_id`**

   Identificador de aplicativo do iTunes.

   * Valor da amostra: `835196493`

* **`a_i_lo`**

   Substituição local do iTunes.

   * Valor da amostra: `jp`

* **`a_dd`**

   Loja padrão para redirecionamento automático.

   * Valor da amostra: `i | g`

* **`a_cid`**

   Substituição de ID personalizado (geralmente o IDFA para iOS ou o ADID para Android).

   * Valor da amostra: `Any String < 255 characters (UTF-8 encoded)`

* **`ctx*`**

   Keys prefixed with `ctx` will be in the context data of the resulting launch hit.

   * Valor da amostra: `ctxmy.custom.key=myValue`

* **`ctxa.referrer.campaign.name`**

   Nome da campanha de aquisição.

   Este parâmetro será necessário se quiser comparar o desempenho de diferentes links de aquisição.

   * Valor da amostra: Conferência da Cimeira de 2015

* **`ctxa.referrer.campaign.trackingcode`**

   Código de rastreamento

   Este parâmetro será necessário se quiser comparar o desempenho de diferentes links de aquisição.

   * Valor da amostra: `lexsxouj`

* **`ctxa.referrer.campaign.source`**

   A fonte.

   * Valor da amostra:Rede de publicidade

* **`ctxa.referrer.campaign.medium`**

   Médio

   * Valor da amostra: Email

* **`ctxa.referrer.campaign.content`**

   Conteúdo

   * Valor da amostra: Imagem nº 325689

* **`ctxa.referrer.campaign.term`**

   Termo

   * Valor da amostra: hiking+boots


Ao criar links de aquisição manualmente, lembre-se das seguintes informações:

* Todos os parâmetros que não correspondem aos parâmetros na tabela são transmitidos como parte do redirecionamento da app store.
* Tecnicamente, todos os parâmetros são opcionais, embora o link não funcione, se pelo menos uma ID de loja for especificada.

   An example of a store ID is `a_g_id`/ `a_i_id`.

* Se a loja de destino não puder ser determinada automaticamente e nenhum padrão for fornecido, um erro 404 será retornado.

