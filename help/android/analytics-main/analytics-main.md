---
description: Essas informações ajudam a usar o Android SDK no Adobe Analytics.
keywords: android;library;mobile;sdk
seo-description: Essas informações ajudam a usar o Android SDK no Adobe Analytics.
seo-title: Visão geral do Analytics
solution: Experience Cloud,Analytics
title: Visão geral do Analytics
topic: Developer and implementation
uuid: cc9fa1d9-bc48-4d03-854a-f7b263580a91
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 73%

---


# Visão geral do Analytics {#analytics}

As informações nesta seção ajudam a usar o Android SDK com o Adobe Analytics.

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para obter a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Criação de identificadores de rastreamento do Analytics

Nos SDKs, identificadores são usados para rastrear usuários, e aqui está a hierarquia de identificadores:

1. Identificador de Visitante personalizado (VID)
2. Identificador de rastreamento do Analytics (AID)
3. Identificador de Experience Cloud (MID)

>[!TIP]
>
>A sigla correta para Identificador da Experience Cloud é ECID. Embora os SDKs ainda usem MID, esse é o nome antigo. 


O AID, que às vezes também é chamado de identificador de rastreamento, é gerado pelo SDK quando o aplicativo não está configurado para usar um MID. O valor persiste entre inicializações e atualizações de aplicativos em `SharedPreferences`. Se o usuário excluir o aplicativo do dispositivo e reinstalar o aplicativo, ou se o desenvolvedor do aplicativo limpar SharedPreferences, um novo identificador é gerado pelo SDK. Esse processo resulta em um novo usuário no relatórios do Analytics.

Para usuários em um aplicativo que introduz o suporte ao serviço de identidade (MID), os valores de AID existentes são enviados com ocorrências do Analytics e a ocorrência do Analytics contém um AID e uma MID. Para novos usuários em um aplicativo com suporte ao serviço de identidade, as solicitações do Analytics contêm apenas uma MID. Para mais informações sobre como identificar visitantes, consulte [Identificação de visitantes](https://docs.adobe.com/content/help/pt-BR/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).