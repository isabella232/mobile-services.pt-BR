---
description: A partir do WatchOS 2, suas extensões WatchKit serão executadas em um dispositivo Apple Watch. Os aplicativos executados neste ambiente exigem a estrutura WatchConnectivity para compartilhar dados com o aplicativo iOS contentor.
seo-description: A partir do WatchOS 2, suas extensões WatchKit serão executadas em um dispositivo Apple Watch. Os aplicativos executados neste ambiente exigem a estrutura WatchConnectivity para compartilhar dados com o aplicativo iOS contentor.
seo-title: Implementação do Apple Watch com o WatchOS 2
solution: Marketing Cloud, Analytics
title: Implementação do Apple Watch com o WatchOS 2
topic: Desenvolvedor e implementação
uuid: 9498467 e-db 5 e -411 e-a 00 e-d 19841 f 485 de
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Apple Watch implementation with WatchOS 2{#apple-watch-implementation-with-watchos}

A partir do watchos 2, suas extensões watchkit podem ser executadas em um Apple Watch. Applications that run in this environment require the `WatchConnectivity` framework to share data with their containing iOS app.

>[!TIP]
>
>A partir `AdobeMobileLibrary` da versão v 4.6.0, `WatchConnectivity` é suportado.

## Introdução {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Certifique-se de ter um projeto com pelo menos as seguintes metas:
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

   `syncSettings:` é chamado na `ADBMobile` biblioteca, que retorna um bool que indica se o dicionário se destina a consumo pela `ADBMobile` biblioteca. Se retornar `No` (Não), a mensagem não foi iniciada a partir do SDK da Adobe.

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

## Configurar a extensão do watchkit {#section_5ADE31741E514330A381F2E3CFD4A814}

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

   `syncSettings:` é chamado na `ADBMobile` biblioteca, que retorna um bool que indica se o dicionário se destina a consumo pela `ADBMobile` biblioteca. Se retornar `NO` (Não), a mensagem não foi iniciada a partir do SDK da Adobe.

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

