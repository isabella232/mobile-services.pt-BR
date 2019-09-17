---
description: O SDK da Adobe usa as APIs de atribuição do aplicativo Search Ads da Apple para permitir que desenvolvedores e profissionais de marketing rastreiem e atribuam downloads de aplicativos originados nas campanhas do Search Ads na Apple App Store.
seo-description: O SDK da Adobe usa as APIs de atribuição do aplicativo Search Ads da Apple para permitir que desenvolvedores e profissionais de marketing rastreiem e atribuam downloads de aplicativos originados nas campanhas do Search Ads na Apple App Store.
seo-title: Anúncios de Pesquisa da Apple
solution: Marketing Cloud,Analytics
title: Anúncios de Pesquisa da Apple
topic: Desenvolvedor e implementação
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
translation-type: tm+mt
source-git-commit: ebcc04ab3e80aafb9d9ec2e1fbc809c743554cb7

---


# Anúncios de Pesquisa da Apple {#apple-search-ads}

O SDK da Adobe usa as APIs de atribuição do aplicativo Search Ads da Apple para permitir que desenvolvedores e profissionais de marketing rastreiem e atribuam downloads de aplicativos originados nas campanhas do Search Ads na Apple App Store. Para obter mais informações sobre as campanhas do Search Ads, consulte [Search Ads da Apple](https://searchads.apple.com).

## Benefícios {#section_CEA30C652AC8470784B8054E299B80FA}

Alguns benefícios do uso dos anúncios da Apple:

* Meça facilmente a eficácia das suas campanhas de download do aplicativo Search Ads, adicionando algumas linhas de código ao seu aplicativo.
* Os desenvolvedores podem acessar a data/hora do download e a palavra-chave da oferta que levou à conversão.

## Implementar anúncios da Apple {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Para implementar os anúncios da Apple, é necessário ter o iOS SDK versão 4.13.2 ou posterior.

Para habilitar seu aplicativo para atribuição do Search Ads:

1. Implementar o Adobe SDK versão 4.13.2 ou superior.

   Para obter mais informações, consulte [Core implementation and lifecycle](/help/ios/getting-started/dev-qs.md).

1. Adicione a estrutura iAd ao arquivo do projeto Xcode para seu aplicativo.

## Relatórios da atribuição do Search Ads {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. Os dados de atribuição do Apple Search Ads são fornecidos no nome da aquisição, na fonte e nos valores do termo.

   If attribution = `true`, all of the `iad-*` fields will be included in the lifecycle hit.

   In addition, the following values will be mapped from the `"iad"` dictionary to our typical acquisition context data fields:

   * `"iad-campaign-id"` --&gt; `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` --&gt; `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` --&gt; `"a.referrer.campaign.content"`
   * `"iad-keyword"` --&gt; `"a.referrer.campaign.term"`
   Esse mapeamento garante que os valores estejam disponíveis em nossos relatórios padrão.
