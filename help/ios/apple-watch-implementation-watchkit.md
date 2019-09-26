---
description: A partir do WatchOS 2, suas extensões WatchKit serão executadas em um dispositivo Apple Watch. Os aplicativos executados neste ambiente exigem a estrutura WatchConnectivity para compartilhar dados com o aplicativo iOS contentor.
seo-description: A partir do WatchOS 2, suas extensões WatchKit serão executadas em um dispositivo Apple Watch. Os aplicativos executados neste ambiente exigem a estrutura WatchConnectivity para compartilhar dados com o aplicativo iOS contentor.
seo-title: Implementação do Apple Watch com o WatchOS 2
solution: Marketing Cloud,Analytics
title: Implementação do Apple Watch com o WatchOS 2
topic: Desenvolvedor e implementação
uuid: 9498467e-db5e-411e-a00e-d19841f485de
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Apple Watch implementation with WatchOS 2{#apple-watch-implementation-with-watchos}

A partir do WatchOS 2, suas extensões WatchKit podem ser executadas em um Apple Watch. Applications that run in this environment require the `WatchConnectivity` framework to share data with their containing iOS app.

>[!TIP]
>
>Starting with `AdobeMobileLibrary` v4.6.0, `WatchConnectivity` is supported.

## New Adobe Experience Platform Mobile SDK Release

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Introdução {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Ensure that you have a project with at least the following targets:
>
>* O aplicativo contêiner
>* O aplicativo WatchKit
>* A extensão do WatchKit
>



Para obter mais informações sobre o desenvolvimento de aplicativos WatchKit, consulte [A arquitetura do aplicativo Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1).

## Configurar o aplicativo contêiner {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

Conclua as seguintes etapas no projeto Xcode:

1. Arraste a pasta `AdobeMobileLibrary` no seu projeto.
1. Ensure that the `ADBMobileConfig.json` file is a member of the containing app’s target.
1. Na guia **[!UICONTROL Criar fases]** do destino do seu aplicativo contêiner, expanda a seção **Link binário com bibliotecas]e adicione as seguintes bibliotecas:[!UICONTROL **

   * `AdobeMobileLibrary.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. Na classe que implementa o protocolo `UIApplicationDelegate`, adicione o protocolo `WCSessionDelegate`.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface AppDelegate : UIResponder <UIApplicationDelegate, WCSessionDelegate>
   ```

1. No arquivo de implementação da sua classe de delegado do aplicativo, importe o `AdobeMobileLibrary`.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. Before making a call to the `ADBMobile` library, in `application:didFinishLaunchingWithOptions:` of your app delegate, configure your `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. In your app delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` é chamado na `ADBMobile` biblioteca, que retorna uma ferramenta que indica se o dicionário foi destinado ao consumo pela `ADBMobile` biblioteca. Se retornar `No` (Não), a mensagem não foi iniciada a partir do SDK da Adobe.

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## Configurar a extensão WatchKit {#section_5ADE31741E514330A381F2E3CFD4A814}

1. Ensure that the `ADBMobileConfig.json` file is a member of your WatchKit extension’s target.
1. Na guia **[!UICONTROL Criar fases]** do destino da sua extensão do WatchKit, expanda a seção **Link binário com bibliotecas]e adicione as seguintes bibliotecas:[!UICONTROL **

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. In your class that implements the `WKExtensionDelegate` protocol, import `WatchConnectivity` and add the `WCSessionDelegate` protocol.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. No arquivo de implementação da sua classe de delegado da extensão, importe o `AdobeMobileLibrary`.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. In `applicationDidFinishLaunching` of your extension delegate, configure your `WCSession` before making any calls to the `ADBMobile` library.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. Em `applicationDidFinishLaunching` do seu delegado de extensão, inicialize o aplicativo Watch para o SDK.

   ```objective-c
   [ADBMobile initializeWatch];
   ```

1. In your extension delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` é chamado na `ADBMobile` biblioteca, que retorna uma ferramenta que indica se o dicionário foi destinado ao consumo pela `ADBMobile` biblioteca. Se retornar `NO` (Não), a mensagem não foi iniciada a partir do SDK da Adobe.

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## Informações adicionais {#section_7BCDB5CF0D424DCA97883753D1881233}

Lembre-se das seguintes informações:

* For WatchKit apps, `a.RunMode` will be set to `Extension`.
* Como os aplicativos WatchKit são executados no relógio, os aplicativos registrarão corretamente seus nomes em `a.AppID`.
* Nenhuma chamada de ciclo de vida é acionada nos aplicativos WatchOS2.

