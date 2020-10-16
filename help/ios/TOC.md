---
product: mobile-services
audience: end-user
user-guide-title: Guia do iOS do Mobile Services
breadcrumb-title: Guia do iOS
translation-type: tm+mt
source-git-commit: 18ef20df0a32741685e35cee98a1adf4a1b823a1
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 99%

---


# Guia do iOS do Mobile Services {#ios}

+ [iOS SDK 4.x para Soluções da Experience Cloud](overview.md)
+ [Notas de versão](rel-notes.md)
+ Introdução {#getting-started-ios}
   + [Visão geral da introdução](getting-started/getting-started.md)
   + [Antes de começar](getting-started/requirements.md)
   + [Implementação principal e ciclo de vida](getting-started/dev-qs.md)
   + [Regras de processamento e dados de contexto](getting-started/proc-rules.md)
   + [Integração Swift](getting-started/swift-integration.md)
   + [Migração para a biblioteca 4.x do iOS](getting-started/migration-v3.md)
+ Configuração {#config-ios}
   + [Visão geral da configuração](configuration/configuration.md)
   + [Configuração JSON do ADBMobile](configuration/json-config/json-config.md)
   + [Substituir o caminho da configuração JSON do ADBMobile](configuration/json-config/json-config-remote.md)
   + [Agrupamento de hits](configuration/hit-batching.md)
   + [Métodos de configuração](configuration/sdk-methods.md)
   + [Segurança de transporte de aplicativos](configuration/app-transport-security.md)
+ [Métricas de ciclo de vida](metrics.md)
+ Analytics {#analytics-ios}
   + [Visão geral do Analytics](analytics-main/analytics-main.md)
   + [Rastrear estados do aplicativo](analytics-main/states.md)
   + [Rastrear ações do aplicativo](analytics-main/actions.md)
   + [Rastreamento de falhas do aplicativo](analytics-main/crashes.md)
   + [Ações cronometradas](analytics-main/timed-actions.md)
   + [Valor vitalício do visitante](analytics-main/lifetime-value.md)
   + Variável products {#products-variable}
      + [Variável products](analytics-main/products/products.md)
      + [Variável products com eVars de merchandising e eventos específicos do produto](analytics-main/products/products-variable-evars-events.md)
   + [Serialização de eventos](analytics-main/event-serialization.md)
   + [Análise de vídeo](analytics-main/video-qs.md)
   + Postbacks {#postbacks}
      + [Visão geral de postbacks](analytics-main/postback/postback.md)
      + [Exemplo de postback](analytics-main/postback/postback-example.md)
      + [Postbacks de PII](analytics-main/postback/c-pii-postbacks.md)
   + [Métodos do Analytics](analytics-main/analytics-methods.md)
+ Aquisição {#acquisition-ios}
   + [Visão geral da aquisição](acquisition-main/acquisition-main.md)
   + [Aquisição de aplicativos móveis](acquisition-main/acquisition.md)
   + [Métodos de aquisição](acquisition-main/c-acquisition-methods.md)
   + Rastreamento de deep links {#tracking-deep-links}
      + [Rastreamento de deep links](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Rastreamento de deep links deferidos de terceiros](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [Testar a aquisição de Links de marketing](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Teste da aquisição V3](acquisition-main/t-testing-version-3-acquisition.md)
   + [Testar a aquisição herdada](acquisition-main/t-testing-acquisition.md)
   + [Anúncios de Pesquisa da Apple](acquisition-main/c-apple-search-ads.md)
+ Mensagens {#messaging-ios}
   + [Visão geral das mensagens](messaging-main/messaging-main.md)
   + Mensagens no aplicativo {#in-app-messaging}
      + [Mensagens no aplicativo](messaging-main/messaging/messaging.md)
      + [Resolução de problemas nas mensagens no aplicativo](messaging-main/messaging/in-apps-ts.md)
   + Mensagens por push {#push-messaging}
      + [Mensagens por push](messaging-main/push-messaging/push-messaging.md)
      + [Implementar mensagens de push com deep linking](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [Receber notificações por push avançadas](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [Resolução de problemas de mensagens por push](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Localização {#location-ios}
   + [Visão geral da localização](location/location.md)
   + [Geolocalização e pontos de interesse](location/geo-poi.md)
   + [Rastreamento iBeacon](location/ibeacon.md)
+ Target {#target-ios}
   + [Visão geral do Target](target-main/target-main.md)
   + [Métodos do Target](target-main/c-target-methods.md)
   + [Realizar uma busca prévia por conteúdos em oferta no iOS](target-main/c-mob-target-prefetch-ios.md)
   + [Visualização do Target no iOS](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Visão geral da Experience Cloud](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Métodos do Adobe Experience Platform Identity Service](marketing-cloud/mc-methods.md)
   + [Device Co-op da Experience Cloud](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Métodos do Audience Manager](amm/aam-methods.md)
+ Implementação da Apple TV com tvOS {#apple-tv-implementation-tvos-ios}
   + [Implementação da Apple TV com tvOS](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [Adobe Target para TVML/TVJS](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [Métodos TVJS](apple-tv-implementation-tvos/tvjs-methods.md)
+ Implementação de extensão do iOS {#ios-ext}
   + [Implementação de extensão do iOS](ios-ext/ios-ext.md)
   + [Implementação de extensão independente](ios-ext/c-stand-alone-extension-implementation.md)
+ [Implementação do Apple Watch com o WatchOS 2](apple-watch-implementation-watchkit.md)
+ Referência de SDK do iOS {#sdk-reference-ios}
   + [Referência de SDK do iOS](reference/reference.md)
   + [IDs da Apple](reference/app-ids.md)
   + [Rastreamento de visitantes entre um aplicativo e a internet móvel](reference/hybrid-app.md)
   + [Versões do dispositivo iOS](reference/device-versions.md)
+ Privacidade e Regulamento Geral sobre a Proteção de Dados {#privacy-gdpr-ios}
   + [Privacidade e Regulamento Geral sobre a Proteção de Dados](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [Recuperação de identificadores armazenados](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [Definição de status de opção do usuário](c-mob-privacy-gdpr-ios/privacy.md)
+ Plug-in PhoneGap {#phonegap-ios}
   + [Plug-in PhoneGap](phonegap/phonegap.md)
   + [Métodos do plug-in PhoneGap](phonegap/phonegap-methods.md)
