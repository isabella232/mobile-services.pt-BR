---
description: O iOS SDK 4.x para as soluções da Experience Cloud permite avaliar aplicativos nativos do iPhone e do iPad da Apple, fornecer conteúdo direcionado dentro dos aplicativos e aproveitar e coletar dados do público-alvo por meio do Audience Manager.
seo-description: O iOS SDK 4.x para as soluções da Experience Cloud permite avaliar aplicativos nativos do iPhone e do iPad da Apple, fornecer conteúdo direcionado dentro dos aplicativos e aproveitar e coletar dados do público-alvo por meio do Audience Manager.
seo-title: iOS SDK 4.x para Soluções da Experience Cloud
solution: Marketing Cloud, Analytics
title: iOS SDK 4.x para Soluções da Experience Cloud
topic: Desenvolvedor e implementação
uuid: 8 b 374 cee -1432-460 b-aac 2-70623 dd 80 a 04
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# iOS SDK 4.x para Soluções da Experience Cloud{#ios-sdk-x-for-experience-cloud-solutions}

O iOS SDK 4.x para as soluções da Experience Cloud permite avaliar aplicativos nativos do iPhone e do iPad da Apple, fornecer conteúdo direcionado dentro dos aplicativos e aproveitar e coletar dados do público-alvo por meio do Audience Manager.

>[!IMPORTANT]
>
>O SKU do Adobe Analytics Mobile Marketing Add-on é necessário para permitir o acesso ao Mobile Services a aquisição móvel, deep linking, geolocalização e recursos de mensagens móveis. Para obter mais informações, entre em contato com o Adobe CSM.

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

   Isso não afeta os dados coletados ou relatados, mas é necessário usar um analisador de pacotes compatível com a inspeção de dados POST para exibir ocorrências.

* If you are upgrading from a previous version (2.x or 3.x), see the [4.x Migration Guide](/help/ios/getting-started/migration-v3.md).

## Documentação do usuário do Adobe Mobile {#section_7583FD5FDED143619048E9744A3F2D21}

O Adobe Mobile Services apresenta uma nova interface do usuário que reúne recursos de marketing para aplicativos para dispositivos móveis em toda a Adobe Experience Cloud. Inicialmente, o serviço Mobile fornece integração simplificada de análises de aplicativos e recursos de definição de metas das soluções Adobe Analytics, Adobe Audience Manager e Adobe Target, e Adobe Experience Platform Identity Service.

Para saber mais sobre a interface do usuário do Adobe Mobile Services e ler a documentação do usuário, consulte [Adobe Mobile Services](/help/using/home.md).

## Usar o Bloodhound

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. A partir de 1º de maio de 2017, não serão fornecidos aprimoramentos e suporte adicionais pela engenharia ou pelo Adobe Expert Care.
