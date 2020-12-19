---
description: O iOS SDK 4.x para as soluções da Experience Cloud permite avaliar aplicativos nativos do iPhone e do iPad da Apple, fornecer conteúdo direcionado dentro dos aplicativos e aproveitar e coletar dados do público usando o Audience Manager.
seo-description: O iOS SDK 4.x para as soluções da Experience Cloud permite avaliar aplicativos nativos do iPhone e do iPad da Apple, fornecer conteúdo direcionado dentro dos aplicativos e aproveitar e coletar dados do público usando o Audience Manager.
seo-title: iOS SDK 4.x para Soluções da Experience Cloud
solution: Experience Cloud,Analytics
title: iOS SDK 4.x para Soluções da Experience Cloud
topic: Developer and implementation
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: tm+mt
source-git-commit: c7400359bc19150926a67b991ba219a7fa187442
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 85%

---


# iOS SDK 4.x para Soluções da Experience Cloud {#ios-sdk-x-for-experience-cloud-solutions}

O iOS SDK 4.x para as soluções da Experience Cloud permite avaliar aplicativos nativos do iPhone e do iPad da Apple, fornecer conteúdo direcionado dentro dos aplicativos e aproveitar e coletar dados do público usando o Audience Manager.

>[!IMPORTANT]
>
>A partir da versão 4.21.0, o iOS SDK tem uma versão mínima exigida do Xcode 12. Se você estiver usando Cocoapods para gerenciar dependências no aplicativo, o SDK do Adobe requer a versão 1.10.0 ou mais recente do Cocoapods.

Se estiver usando a versão 4.21.0 ou mais recente, leia a documentação com as seguintes alterações em mente:

* Sempre que um arquivo de biblioteca binária for mencionado, sua substituição XCFrframework deve ser usada em vez disso:
   * `AdobeMobileLibrary.a` > `AdobeMobile.xcframework`
   * `AdobeMobileLibrary_Extension.a` >  `AdobeMobileExtension.xcframework`
   * `AdobeMobileLibrary_Watch.a` >  `AdobeMobileWatch.xcframework`
   * `AdobeMobileLibrary_TV.a` >  `AdobeMobileTV.xcframework`
* Se você adicionar manualmente o Adobe XCFrameworks ao seu projeto, verifique se eles não estão incorporados.

>[!IMPORTANT]
>
>O SKU do Adobe Analytics Mobile Marketing Add-on é necessário para habilitar o Mobile Services para aquisição móvel, deep linking, geolocalização e mensagens móveis. Para obter mais informações, entre em contato com seu CSM da Adobe.

>[!IMPORTANT]
>
>O iOS SDK 4.x para Soluções da Experience Cloud agora é compatível com [iOS 13 e Xcode 11](https://developer.apple.com/ios/). Para garantir compatibilidade perfeita, use as versões mais recentes dos SDKs 4.x do iOS. Para obter mais informações sobre a versão mais recente, consulte as [notas de versão](/help/ios/rel-notes.md).

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para obter a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

Algumas informações para lembrar:

* Há suporte para iOS 8 ou posterior.

   Para o iOS 11 ou posterior, você **deve** ter o SDK versão 4.13.8 ou posterior.

* Na versão 4.2 e posterior deste SDK, todas as ocorrências são enviadas usando HTTP POST.

   Isso não afeta os dados coletados ou relatados, mas você deve usar um analisador de pacotes compatível com a inspeção de dados POST para ver as ocorrências.

* Se estiver atualizando de uma versão anterior (2.x ou 3.x), consulte o [Guia de migração 4.x](/help/ios/getting-started/migration-v3.md).

## Documentação do usuário do Adobe Mobile {#section_7583FD5FDED143619048E9744A3F2D21}

O Adobe Mobile Services apresenta uma nova interface do usuário que reúne recursos de marketing para aplicativos para dispositivos móveis em toda a Adobe Experience Cloud. Inicialmente, o Adobe Mobile Services fornece integração perfeita dos aplicativos de análise com recursos de direcionamento das soluções do Adobe Analytics, do Adobe Audience Manager, do Adobe Target e do Adobe Experience Platform Identity Service.

Para saber mais sobre a interface do usuário do Adobe Mobile Services e ler a documentação do usuário, consulte [Adobe Mobile Services](/help/using/home.md).

## Usar o Bloodhound

>[!IMPORTANT]
>
>Em **30 de abril de 2017**, o Adobe Bloodhound foi interrompido. A partir de 1º de maio de 2017, não serão fornecidos aprimoramentos e suporte adicionais pela engenharia ou pelo Adobe Expert Care.
