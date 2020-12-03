---
description: O SDK da Adobe usa as APIs de atribuição do aplicativo Search Ads da Apple para permitir que desenvolvedores e profissionais de marketing rastreiem e atribuam downloads de aplicativos originados nas campanhas do Search Ads na Apple App Store.
seo-description: O SDK da Adobe usa as APIs de atribuição do aplicativo Search Ads da Apple para permitir que desenvolvedores e profissionais de marketing rastreiem e atribuam downloads de aplicativos originados nas campanhas do Search Ads na Apple App Store.
seo-title: Anúncios de Pesquisa da Apple
solution: Experience Cloud,Analytics
title: Anúncios de Pesquisa da Apple
topic: Developer and implementation
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 100%

---


# Anúncios de Pesquisa da Apple {#apple-search-ads}

O SDK da Adobe usa as APIs de atribuição do aplicativo Search Ads da Apple para permitir que desenvolvedores e profissionais de marketing rastreiem e atribuam downloads de aplicativos originados nas campanhas do Search Ads na Apple App Store. Para obter mais informações sobre as campanhas do Search Ad, consulte [Apple Search Ads](https://searchads.apple.com).

## Benefícios {#section_CEA30C652AC8470784B8054E299B80FA}

Alguns benefícios do uso dos anúncios da Apple:

* Meça facilmente a eficácia das suas campanhas de download do aplicativo Search Ads, adicionando algumas linhas de código ao seu aplicativo.
* Os desenvolvedores podem acessar a data/hora do download e a palavra-chave da oferta que levou à conversão.

## Implementar anúncios da Apple {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Para implementar os anúncios da Apple, você deve ter o SDK do iOS versão 4.13.2 ou posterior.

Para habilitar seu aplicativo para atribuição do Search Ads:

1. Implemente o Adobe SDK versão 4.13.2 ou superior.

   Para obter mais informações, consulte [Implementação principal e ciclo de vida](/help/ios/getting-started/dev-qs.md).

1. Adicione a estrutura iAd ao arquivo do projeto Xcode para seu aplicativo.

## Relatórios da atribuição do Search Ads {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. Os dados de atribuição do Apple Search Ads são fornecidos no nome da aquisição, na fonte e nos valores do termo.

   Se a atribuição = `true`, todos os campos `iad-*` serão incluídos na ocorrência de ciclo de vida.

   Além disso, os seguintes valores serão mapeados do dicionário `"iad"` para nossos campos de dados de contexto de aquisição típicos:

   * `"iad-campaign-id"` --> `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` --> `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` --> `"a.referrer.campaign.content"`
   * `"iad-keyword"` --> `"a.referrer.campaign.term"`
   Esse mapeamento assegura que os valores estejam disponíveis em nossos relatórios padrão.
