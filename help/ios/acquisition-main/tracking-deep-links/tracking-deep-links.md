---
description: Essas informações podem ser usadas para rastrear deep links e deep links deferidos nos aplicativos móveis usando o SDK do iOS do Adobe Mobile.
seo-description: Essas informações podem ser usadas para rastrear deep links e deep links deferidos nos aplicativos móveis usando o SDK do iOS do Adobe Mobile.
seo-title: Rastreamento de deep links
solution: Marketing Cloud, Analytics
title: Rastreamento de deep links
uuid: 08 dc 2820-7 fd 3-419 f-ac 2 d-dcf 12532578 a
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Tracking deep links{#tracking-deep-links}

Essas informações podem ser usadas para rastrear deep links e deep links deferidos nos aplicativos móveis usando o SDK do iOS do Adobe Mobile.

Para obter mais informações sobre como os profissionais de marketing usam deep linking em seus aplicativos, consulte [Aquisição](/help/ios/acquisition-main/acquisition.md) na documentação dos Mobile Services.

## Rastreamento de deep links

1. Adicione o SDK ao seu projeto e implemente as medições de ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o Arquivo de configuração ao projeto* na [Implementação principal e no ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Registre o aplicativo para lidar com Comunicações entre aplicativos ou Suporte a Links universais.

   Para obter mais informações, consulte [Comunicações entre aplicativos](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10) ou [Suporte Universal Links](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)

1. Rastrear deep links em openURL.

   Este é um exemplo de rastreamento de deep link:

   ```objective-c
   - (BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
       return YES; 
   } 
   - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
   
       return YES; 
   }
   ```

The Adobe Mobile SDK can parse key and value pairs of data appended to any deep or Universal Link, provided that the link contains a key with a `a.deeplink.id` label and a corresponding non-null and user generated value. Todos os pares de chaves e valores de dados adicionados ao link serão analisados, anexados a uma ocorrência de ciclo de vida e enviados ao Adobe Analytics, desde que o link contenha a chave e valor `a.deeplink.id`.

Você também pode optar por anexar uma ou mais das seguintes chaves reservadas (com valores gerados pelo usuário) ao deep link ou Link universal:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Essas chaves são variáveis pré-mapeadas para relatórios no Adobe Analytics. Para obter mais informações sobre regras de mapeamento e processamento, consulte [Regras de processamento e Dados de contexto](/help/ios/getting-started/proc-rules.md).

### Rastreamento de deep links adiados

1. Registre o retorno de chamada de dados da Adobe.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. Lidar `ADBMobileDataEventDeepLink``AdobeDataCallback`com.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
       if (event == ADBMobileDataEventDeepLink) { 
           [self handleDeepLink:adobeData[ADBConfigKeyCallbackDeepLink]]; 
       } 
   }];
   ```

## Deep link public information {#section_44600E9AA68D4A53AA0C14BD86CC5284}

### Métodos

```objective-c
/** 
 * @brief Tracks a Adobe Deep Link click-through 
 * @param url The URL resource received from UIApplication delegate method. 
 * @note Adobe Link data will be appended to the lifecycle call if it is a launch event, otherwise an extra call will be sent. 
 */ 
+ (void) trackAdobeDeepLink:(nullable NSURL *)url;
```

#### Constantes

```objective-c
/* 
 * Used within ADBMobileDataCallback 
 * Key for deep link URL. 
 */ 
FOUNDATION_EXPORT NSString *const __nonnull ADBConfigKeyCallbackDeepLink;
```

