---
description: Use o SDK do iOS para implementar o rastreamento de deep links deferidos de terceiros.
seo-description: Use o SDK do iOS para implementar o rastreamento de deep links deferidos de terceiros.
seo-title: Rastreamento de deep links deferidos de terceiros
title: Rastreamento de deep links deferidos de terceiros
uuid: 5525 b 609-e 926-44 b 9-b 0 f 5-38 e 9 dd 7 c 9761
translation-type: tm+mt
source-git-commit: 4b5be6c51c716114e597a80d475f838e23abb1b1

---


# Tracking third-party deferred deep links {#tracking-third-party-deferred-deep-links}

Use o SDK do iOS para implementar o rastreamento de deep links deferidos de terceiros.

## Classic Adobe Mobile SDK deep linking {#section_D114FA1EB9664EAA82E036A990694B26}

The Adobe Mobile SDK currently supports deep linking where the app developer is expected to call the `trackAdobeDeepLink` API and pass the deep linking URL, which is the fingerprinter URL that is generated in Adobe Mobile Services during configuration. O SDK consulta a impressão digital para obter dados de aquisição e os anexa aos dados de contexto das chamadas de análise de instalação/inicialização como parte do ciclo de vida. Além disso, o SDK também anexa os dados de deep links dos parâmetros de URL deeplink. Para obter mais informações sobre deep linking, consulte [Rastreamento de deep links](/help/ios/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Facebook deep linking {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Um criador de anúncios pode criar um anúncio no Facebook como um deep link. Quando os usuários clicam no anúncio no Facebook, são direcionados diretamente para a informação em que estão interessados no aplicativo. O deep link **não** é um URL de impressão digital. No entanto, durante a configuração do anúncio, existe uma opção para fornecer um URL de deep link de terceiros. Um desenvolvedor de aplicativos, que esteja usando os SDKs e os serviços do Experience Cloud Mobile, deve inserir o URL de impressão digital dos Mobile Services configurado neste campo. Se tudo estiver configurado corretamente, o SDK do Facebook transmite esse URL para o aplicativo quando ele for instalado ou iniciado.

## Configurar os SDKs {#section_834CD3109175432B8173ECB6EA7DE315}

1. Configure o SDK do Facebook.

   Para obter mais informações, consulte o seguinte:

   * [Introdução ao SDK do Facebook para iOS](https://developers.facebook.com/docs/ios/getting-started)
   * [Configuração de deeplinking](https://developers.facebook.com/docs/app-ads/deep-linking#os)

1. Para configurar o SDK, chame `trackAdobeDeepLink` e transmita o URL para os sdks:

   ```objective-c
   - (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation 
   { 
     [ADBMobile trackAdobeDeepLink:url]; 
     return YES; 
   }
   ```

   >[!TIP]
   >
   >Ensure that the deep link URL has a key with the name `a.deeplink.id`. Nenhum parâmetro de URL será anexado aos dados de contexto se o URL perder o parâmetro `a.deeplink.id`.

Se o aplicativo estiver configurado conforme descrito acima, a versão atual do AMSDK funcionará corretamente e anexará os dados do deep link às chamadas de análise de instalação/inicialização apropriadamente.

## Ativar o recurso em um aplicativo de amostra {#section_64C15E269E89424B8E3D029F88094620}

1. Registre um esquema de URL.

   Certifique-se de ter registrado um esquema de URL, que é o mesmo que o URL de deep link.

   ```objective-c
   <key>CFBundleURLTypes</key> 
       <array> 
           <dict> 
               <key>CFBundleURLSchemes</key> 
               <array> 
                   <string>sampleapptest</string> 
               </array> 
           </dict> 
       </array>
   ```

1. Vincule os SDKs do Facebook.

   ![Ativos do Facebook](assets/link-fb-sdk.jpg)

1. Editar `AppDelegate`.

   1. Importe os cabeçalhos.

      ```objective-c
      /************************************************************************* 
      ADOBE SYSTEMS INCORPORATED 
      Copyright 2015 Adobe Systems Incorporated 
      All Rights Reserved. 
      NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the 
      terms of the Adobe license agreement accompanying it.  If you have received this file from a 
      source other than Adobe, then your use, modification, or distribution of it requires the prior 
      written permission of Adobe. 
      
      **************************************************************************/ 
      
      #import "AppDelegate.h" 
      #import "GalleryViewController.h" 
      #import "SimpleTrackingController.h" 
      #import "PostbackController.h" 
      #import "InAppMessageViewController.h" 
      #import "LifetimeValueController.h" 
      #import "LocationTargetingController.h" 
      #import "MediaViewController.h" 
      #import "TimedActionController.h"
      
      // Uncomment after including the facebook sdks. 
      @import FBSDKCoreKit; 
      @import Bolts;
      ```

   1. Adicione a alça para deep links deferidos.

      ```objective-c
      - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
          /* 
           * Adobe Tracking - Analytics 
           * 
           * turn on debug logging for the ADBMobile SDK 
           * enable the collection of lifecycle data 
           */ 
              if (launchOptions[UIApplicationLaunchOptionsURLKey] == nil) { 
                  if (NSClassFromString(@"FBSDKAppLinkUtility") != nil) 
                  { 
                      [NSClassFromString(@"FBSDKAppLinkUtility") performSelector:@selector(fetchDeferredAppLink:) withObject:^(NSURL *url, NSError *error) { 
                          if (error) { 
                              NSLog(@"Received error while fetching deferred app link %@", error); 
                          } 
                          if (url) { 
                              [[UIApplication sharedApplication] openURL:url]; 
                          } 
                      }]; 
                  } 
          } 
          ..... 
          ..... 
          return YES; 
      }
      ```

   1. Chame a `trackAdobeDeepLink` API e transmita o URL do deep link para o SDK.

      ```objective-c
      - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
          [self handleDeepLink:url]; 
      
          return YES; 
      }
      ```

