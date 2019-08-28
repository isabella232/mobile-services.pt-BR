---
description: Esta informação ajuda a implementar a Apple TV com tvOS.
seo-description: Esta informação ajuda a implementar a Apple TV com tvOS.
seo-title: Implementação da Apple TV com tvOS
solution: Marketing Cloud, Analytics
title: Implementação da Apple TV com tvOS
topic: Desenvolvedor e implementação
uuid: d 1571 ea 2-a 5 de -4 b 96-a 527-72 abbf 51 fab 8
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Apple TV implementation with tvOS {#apple-tv-implementation-with-tvos}

Esta informação ajuda a implementar a Apple TV com tvOS.

## Nova versão do SDK da Adobe Experience Cloud

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para começar, acesse o Launch.
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Para obter mais informações, consulte [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

Com a Apple TV, agora você pode criar aplicativos para serem executados no ambiente tvOS nativo. Você pode criar um aplicativo nativo usando várias estruturas no iOS, ou você pode criar seu aplicativo usando modelos XML e JavaScript.

>[!TIP]
>
>O suporte tvos está disponível a partir `AdobeMobileLibrary` da versão 4.7.0.

## Introdução {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>Supomos que seu projeto tenha uma meta que seja um aplicativo da Apple TV direcionado ao tvos. Para obter mais informações, consulte [tvOS](https://developer.apple.com/tvos/documentation/).

## Configure a native app for tvOS {#section_5095F19B3C4545F68E8C1E37A7E303AE}

Conclua as seguintes etapas no projeto Xcode:

1. Arraste a pasta AdobeMobileLibrary no seu projeto.
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. Na guia **[!UICONTROL Criar fases]** do destino do seu aplicativo tvOS, expanda a seção **Link binário com bibliotecas]e adicione as seguintes bibliotecas:[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

Para obter informações, consulte a documentação do iOS em [iOS](https://developer.apple.com/ios/resources/).

## Configure a TVML/TVJS app for tvOS {#section_AB2EC8C326654F3387658EBBD990BB12}

1. Arraste a pasta `AdobeMobileLibrary` no seu projeto.
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. Na guia **[!UICONTROL Criar fases]** do destino do seu aplicativo tvOS, expanda a seção **Link binário com bibliotecas]e adicione as seguintes bibliotecas:[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. No arquivo de implementação da sua classe `TVApplicationControllerDelegate`, importe o SDK.

   ```objective-c
   #import “ADBMobile.h"
   ```

1. In the `application:didFinishLaunchWithOptions:` method of your `TVApplicationControllerDelegate` class, pass your `TVApplicationController` object to the SDK with the `installTVMLHooks:` method.

   O SDK da Adobe precisa acessar o `TVApplicationController` do aplicativo para se registrar no JSContext do aplicativo. Esta etapa permite que você chame os métodos nativos no SDK da Adobe a partir de seus arquivos JavaScript.

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. Nos seus arquivos JavaScript, use o objeto `ADBMobile` para acessar os métodos nativos do Adobe SDK.

   For a complete listing of the available methods, see [TVJS Methods](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md).

