---
description: A partir do WatchOS 2, suas extensões WatchKit serão executadas em um dispositivo Apple Watch dispositivo. Os aplicativos executados neste ambiente exigem a estrutura WatchConnectivity para compartilhar dados com o aplicativo iOS.
seo-description: A partir do WatchOS 2, suas extensões WatchKit serão executadas em um dispositivo Apple Watch dispositivo. Os aplicativos executados neste ambiente exigem a estrutura WatchConnectivity para compartilhar dados com o aplicativo iOS.
seo-title: Implementação do Apple Watch com o WatchOS 2
solution: Experience Cloud,Analytics
title: Implementação do Apple Watch com o WatchOS 2
topic: Developer and implementation
uuid: 9498467e-db5e-411e-a00e-d19841f485de
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 100%

---


# Implementação do Apple Watch com o WatchOS 2 {#apple-watch-implementation-with-watchos}

A partir do WatchOS 2, suas extensões WatchKit serão executadas em um dispositivo Apple Watch. Os aplicativos executados neste ambiente exigem a estrutura `WatchConnectivity` para compartilhar dados com o aplicativo iOS contentor.

>[!TIP]
>
>A partir da `AdobeMobileLibrary` v4.6.0, há suporte para `WatchConnectivity`.

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para obter a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Introdução {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Certifique-se de ter um projeto com pelo menos os seguintes destinos:
>
>* O aplicativo contendo
>* O aplicativo WatchKit
>* A extensão WatchKit
>



Para obter mais informações sobre como desenvolver aplicativos WatchKit, consulte [A arquitetura do aplicativo Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1).

## Configurar o aplicativo contêiner {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

Conclua as seguintes etapas no projeto Xcode:

1. Arraste a pasta `AdobeMobileLibrary` no seu projeto.
1. Certifique-se de que o arquivo `ADBMobileConfig.json` é um membro do destino do seu aplicativo contêiner.
1. Na guia **[!UICONTROL Criar fases]** do destino do seu aplicativo contêiner, expanda a seção **[!UICONTROL Link binário com bibliotecas]** e adicione as seguintes bibliotecas:

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

1. Antes de chamar a biblioteca `ADBMobile`, em `application:didFinishLaunchingWithOptions:` do delegado do aplicativo, configure `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. No delegado do aplicativo, implemente os métodos `session:didReceiveMessage:` e `session:didReceiveUserInfo:`.

   `syncSettings:` é chamado na biblioteca `ADBMobile`, que retorna um bool indicando se o dicionário deve ser consumido pela biblioteca `ADBMobile`. Se retornar `No` (Não), a mensagem não foi iniciada a partir do SDK da Adobe.

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

1. Certifique-se de que o arquivo `ADBMobileConfig.json` é um membro do destino da sua extensão.
1. Na guia **[!UICONTROL Criar fases]** do destino da sua extensão do WatchKit, expanda a seção **[!UICONTROL Link binário com bibliotecas]** e adicione as seguintes bibliotecas:

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. Na classe que implementa o protocolo `WKExtensionDelegate`, importe `WatchConnectivity` e adicione o protocolo `WCSessionDelegate`.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. No arquivo de implementação da sua classe de delegado da extensão, importe o `AdobeMobileLibrary`.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. Em `applicationDidFinishLaunching` do delegado de extensão, configure `WCSession` antes de chamar a biblioteca `ADBMobile`.

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

1. No delegado de extensão, implemente os métodos `session:didReceiveMessage:` e `session:didReceiveUserInfo:`.

   `syncSettings:` é chamado na biblioteca `ADBMobile`, que retorna um bool indicando se o dicionário deve ser consumido pela biblioteca `ADBMobile`. Se retornar `NO` (Não), a mensagem não foi iniciada a partir do SDK da Adobe.

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

* Para os aplicativos WatchKit, `a.RunMode` será definido para `Extension`.
* Como os aplicativos WatchKit são executados no relógio, os aplicativos registrarão corretamente seus nomes em `a.AppID`.
* Nenhuma chamada de ciclo de vida é acionada nos aplicativos WatchOS2.

