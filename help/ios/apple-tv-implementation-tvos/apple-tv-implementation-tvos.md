---
description: Esta informação ajuda a implementar a Apple TV com tvOS.
seo-description: Esta informação ajuda a implementar a Apple TV com tvOS.
seo-title: Implementação da Apple TV com tvOS
solution: Experience Cloud,Analytics
title: Implementação da Apple TV com tvOS
topic-fix: Developer and implementation
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
exl-id: 35b7f02d-ae48-4c6f-9a3a-6d106a1026ad
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 100%

---

# Implementação da Apple TV com tvOS {#apple-tv-implementation-with-tvos}

Esta informação ajuda a implementar a Apple TV com tvOS.

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para obter a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Visão geral

Com a Apple TV, agora é possível criar aplicativos para execução no ambiente tvOS nativo. Você pode criar um aplicativo nativo usando várias estruturas no iOS ou pode criar seu aplicativo usando modelos XML e JavaScript.

>[!TIP]
>
>O suporte para tvOS está disponível a partir da `AdobeMobileLibrary` versão 4.7.0.

## Introdução {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>Supomos que seu projeto tenha um destino que seja um aplicativo da Apple TV direcionado ao tvOS. Para obter mais informações, consulte [tvOS](https://developer.apple.com/tvos/documentation/).

## Configurar um aplicativo nativo para tvOS {#section_5095F19B3C4545F68E8C1E37A7E303AE}

Conclua as seguintes etapas no projeto Xcode:

1. Arraste a pasta AdobeMobileLibrary no seu projeto.
1. Certifique-se de que o arquivo `ADBMobileConfig.json` é um membro do destino.
1. Na guia **[!UICONTROL Criar fases]** do destino do seu aplicativo tvOS, expanda a seção **[!UICONTROL Link binário com bibliotecas]** e adicione as seguintes bibliotecas:

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

Para obter informações, consulte a documentação do iOS em [iOS](https://developer.apple.com/ios/resources/).

## Configurar um aplicativo TVML/TVJS para tvOS {#section_AB2EC8C326654F3387658EBBD990BB12}

1. Arraste a pasta `AdobeMobileLibrary` no seu projeto.
1. Certifique-se de que o arquivo `ADBMobileConfig.json` é um membro do destino.
1. Na guia **[!UICONTROL Criar fases]** do destino do seu aplicativo tvOS, expanda a seção **[!UICONTROL Link binário com bibliotecas]** e adicione as seguintes bibliotecas:

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. No arquivo de implementação da sua classe `TVApplicationControllerDelegate`, importe o SDK.

   ```objective-c
   #import “ADBMobile.h"
   ```

1. No método `application:didFinishLaunchWithOptions:` da classe `TVApplicationControllerDelegate`, transmita o objeto `TVApplicationController` ao SDK com o método `installTVMLHooks:`.

   O SDK da Adobe precisa acessar o `TVApplicationController` do aplicativo para se registrar no JSContext do aplicativo. Esta etapa permite que você chame os métodos nativos no SDK da Adobe a partir de seus arquivos JavaScript.

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. Nos seus arquivos JavaScript, use o objeto `ADBMobile` para acessar os métodos nativos do Adobe SDK.

   Para obter uma lista completa dos métodos disponíveis, consulte [Métodos TVJS](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md).
