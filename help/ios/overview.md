---
description: O iOS SDK 4.x para as soluções da Experience Cloud permite avaliar aplicativos nativos do iPhone e do iPad da Apple, fornecer conteúdo direcionado dentro dos aplicativos e aproveitar e coletar dados do público-alvo por meio do Audience Manager.
seo-description: O iOS SDK 4.x para as soluções da Experience Cloud permite avaliar aplicativos nativos do iPhone e do iPad da Apple, fornecer conteúdo direcionado dentro dos aplicativos e aproveitar e coletar dados do público-alvo por meio do Audience Manager.
seo-title: iOS SDK 4.x para Soluções da Experience Cloud
solution: Marketing Cloud,Analytics
title: iOS SDK 4.x para Soluções da Experience Cloud
topic: Desenvolvedor e implementação
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: tm+mt
source-git-commit: 0f6eec995626f4c93f56d59b682083bd0428d9e1

---


# iOS SDK 4.x para Soluções da Experience Cloud{#ios-sdk-x-for-experience-cloud-solutions}

O iOS SDK 4.x para as soluções da Experience Cloud permite avaliar aplicativos nativos do iPhone e do iPad da Apple, fornecer conteúdo direcionado dentro dos aplicativos e aproveitar e coletar dados do público-alvo por meio do Audience Manager.

>[!IMPORTANT]
>
>The Adobe Analytics Mobile Marketing Add-on SKU is required to enable Mobile Services access to mobile acquisition, deep linking, geolocation, and mobile messaging capabilities. For more information, contact your Adobe CSM.

>[!IMPORTANT]
>
>The iOS SDK 4.x for Experience Cloud Solutions is now supports [iOS 13 and Xcode 11][https://developer.apple.com/ios/]. To ensure seamless compatibility, use the latest versions of the 4.x iOS SDKs. For more information about the latest version, see the [release notes](/help/ios/rel-notes.md).

## Nova versão do SDK da Adobe Experience Cloud

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para começar, acesse o Launch.
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Para obter mais informações, consulte [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

Algumas informações para lembrar:

* Há suporte para iOS 5 ou posteriores

   Para iOS 11 ou posteriores, é **necessário** ter a versão 4.13.8 ou posteriores do SDK.

* Na versão 4.2 e posterior deste SDK, todas as ocorrências são enviadas usando HTTP POST.

   Isso não afeta os dados coletados ou reportados, mas é necessário usar um analisador de pacotes compatível com a inspeção de dados POST para visualizar as ocorrências.

* If you are upgrading from a previous version (2.x or 3.x), see the [4.x Migration Guide](/help/ios/getting-started/migration-v3.md).

## Documentação do usuário do Adobe Mobile {#section_7583FD5FDED143619048E9744A3F2D21}

O Adobe Mobile Services apresenta uma nova interface do usuário que reúne recursos de marketing para aplicativos para dispositivos móveis em toda a Adobe Experience Cloud. Inicialmente, o Mobile Service fornece integração perfeita entre os recursos de análise e segmentação de aplicativos das soluções do Adobe Analytics, Adobe Audience Manager e Adobe Target e Adobe Experience Platform Identity Service.

Para saber mais sobre a interface do usuário do Adobe Mobile Services e ler a documentação do usuário, consulte [Adobe Mobile Services](/help/using/home.md).

## Usar o Bloodhound

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. A partir de 1º de maio de 2017, não serão fornecidos aprimoramentos e suporte adicionais pela engenharia ou pelo Adobe Expert Care.
