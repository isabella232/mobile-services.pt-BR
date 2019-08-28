---
description: Essas informações ajudam a usar o Android SDK no Adobe Analytics.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: Essas informações ajudam a usar o Android SDK no Adobe Analytics.
seo-title: Visão geral do Analytics
solution: Marketing Cloud, Analytics
title: Visão geral do Analytics
topic: Desenvolvedor e implementação
uuid: cc 9 fa 1 d 9-bc 48-4 d 03-854 a-f 7 b 263580 a 91
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visão geral do Analytics {#analytics}

As informações nesta seção ajudam você a usar o Android SDK com o Adobe Analytics.

## Nova versão do SDK da Adobe Experience Cloud

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

>[!IMPORTANT]
>
>Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para começar, acesse o [Launch](https://launch.adobe.com/).
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Geração de identificadores de rastreamento do Analytics

Nos SDKs, identificadores são usados para rastrear usuários. Veja a seguir a hierarquia de identificadores:

1. Identificador de visitante personalizado (VID)
2. Identificador de rastreamento do Analytics (AID)
3. Identificador da Experience Cloud (MID)

>[!TIP]
>
>O acrônimo correto para Identificador da Experience Cloud é ECID. Embora os SDKs ainda usem MID, esse é o nome antigo.

O AID, que às vezes também é chamado de identificador de rastreamento, é gerado pelo SDK quando o aplicativo não está configurado para usar um MID. O valor persiste entre inicializações e atualizações de aplicativos em `SharedPreferences`. Se o usuário excluir o aplicativo do dispositivo e reinstalar o aplicativo, ou se o desenvolvedor do aplicativo limpar SharedPreferences, um novo identificador é gerado pelo SDK. Esse processo resulta em um novo usuário nos relatórios do Analytics.

Para usuários em um aplicativo que introduz o suporte ao serviço de identidade (MID), os valores de AID existentes são enviados com ocorrências do Analytics, e a ocorrência do Analytics contém um AID e um MID. Para novos usuários em um aplicativo com suporte ao serviço de identidade, as solicitações do Analytics contêm apenas um MID. For more information about identifying visitors, see [Identify visitors](https://docs.adobe.com/content/help/en/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).