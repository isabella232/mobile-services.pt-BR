---
description: Essas informações podem ser usadas para rastrear deep links e deep links deferidos nos aplicativos móveis usando o SDK do iOS do Adobe Mobile.
solution: Experience Cloud,Analytics
title: Rastreamento de deep links
uuid: 08dc2820-7fd3-419f-ac2d-dcf12532578a
exl-id: a8b20233-d800-4318-ad4f-39229d8b3a5e
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 100%

---

# Rastreamento de deep links{#tracking-deep-links}

Essas informações podem ser usadas para rastrear deep links e deep links deferidos nos aplicativos móveis usando o SDK do iOS do Adobe Mobile.

Para obter mais informações sobre como os profissionais de marketing usam deep linking em seus aplicativos, consulte [Aquisição](/help/ios/acquisition-main/acquisition.md) na documentação dos Mobile Services.

## Rastreamento de deep links

1. Adicione o SDK ao seu projeto e implemente as medições de ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao seu projeto* em [Implementação principal e Ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Registre o aplicativo para gerenciar comunicações entre aplicativos ou suportar links universais.

   Para obter mais informações, consulte [Comunicações entre aplicativos](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10) ou [Links universais de suporte](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)

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

O SDK do Adobe Mobile pode analisar pares de chaves e valores de dados adicionados a qualquer deep link ou link universal, desde que o link contenha uma chave com um rótulo `a.deeplink.id` e um valor não-nulo correspondente gerado pelo usuário. Todos os pares de chaves e valores de dados adicionados ao link serão analisados, anexados a uma ocorrência de ciclo de vida e enviados ao Adobe Analytics, desde que o link contenha a chave e valor `a.deeplink.id`.

Além disso, você também pode optar por adicionar uma ou mais das seguintes chaves reservadas (com valores gerados pelo usuário) ao deep link ou link universal:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Essas chaves são variáveis pré-mapeadas para relatórios no Adobe Analytics. Para obter mais informações sobre regras de mapeamento e processamento, consulte [Regras de processamento e dados de contexto](/help/ios/getting-started/proc-rules.md).

### Rastreamento de deep links deferidos

1. Registre o retorno de chamada de dados da Adobe.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. Processe `ADBMobileDataEventDeepLink` dentro de `AdobeDataCallback`.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
       if (event == ADBMobileDataEventDeepLink) { 
           [self handleDeepLink:adobeData[ADBConfigKeyCallbackDeepLink]]; 
       } 
   }];
   ```

## Informações públicas do deep link {#section_44600E9AA68D4A53AA0C14BD86CC5284}

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
