---
product: mobile-services
audience: usuário final
user-guide-title: Ajuda para iOS do Mobile Services
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Ajuda para iOS do Mobile Services {#ios}

+ [iOS SDK 4.x para Soluções da Experience Cloud](overview.md)
+ [Notas de versão](rel-notes.md)
+ Introdução {#getting-started-ios}
   + [Visão geral de introdução](getting-started/getting-started.md)
   + [Antes de começar](getting-started/requirements.md)
   + [Implementação principal e ciclo de vida](getting-started/dev-qs.md)
   + [Regras de processamento e dados de contexto](getting-started/proc-rules.md)
   + [Integração Swift](getting-started/swift-integration.md)
   + [Migração para a biblioteca iOS. x do iOS](getting-started/migration-v3.md)
+ Configuração {#config-ios}
   + [Visão geral de configuração](configuration/configuration.md)
   + [Configuração JSON do adbmobile](configuration/json-config/json-config.md)
   + [Substituir o caminho de configuração JSON do adbmobile](configuration/json-config/json-config-remote.md)
   + [Agrupamento de hits](configuration/hit-batching.md)
   + [Métodos de configuração](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [Medições de ciclo de vida](metrics.md)
+ Analytics {#analytics-ios}
   + [Visão geral do Analytics](analytics-main/analytics-main.md)
   + [Rastrear estados do aplicativo](analytics-main/states.md)
   + [Rastrear ações do aplicativo](analytics-main/actions.md)
   + [Rastreamento de falhas do aplicativo](analytics-main/crashes.md)
   + [Ações cronometradas](analytics-main/timed-actions.md)
   + [Valor do tempo de vida do visitante](analytics-main/lifetime-value.md)
   + Products variable {#products-variable}
      + [Variável products](analytics-main/products/products.md)
      + [Variável products com evars de merchandising e eventos específicos do produto](analytics-main/products/products-variable-evars-events.md)
   + [Serialização de eventos](analytics-main/event-serialization.md)
   + [Análise de vídeo](analytics-main/video-qs.md)
   + Postbacks {#postbacks}
      + [Visão geral de postbacks](analytics-main/postback/postback.md)
      + [Exemplo de postback](analytics-main/postback/postback-example.md)
      + [postbacks de PII](analytics-main/postback/c-pii-postbacks.md)
   + [Métodos do Analytics](analytics-main/analytics-methods.md)
+ Aquisição {#acquisition-ios}
   + [Visão geral da aquisição](acquisition-main/acquisition-main.md)
   + [Aquisição de aplicativos móveis](acquisition-main/acquisition.md)
   + [Métodos de aquisição](acquisition-main/c-acquisition-methods.md)
   + Tracking deep links {#tracking-deep-links}
      + [Rastreamento de deep links](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Rastreamento de deep links adiados de terceiros](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [Testar a aquisição do link de marketing](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Teste de aquisição V 3](acquisition-main/t-testing-version-3-acquisition.md)
   + [Teste da aquisição herdada](acquisition-main/t-testing-acquisition.md)
   + [Anúncios de Pesquisa da Apple](acquisition-main/c-apple-search-ads.md)
+ Mensagens {#messaging-ios}
   + [Visão geral de mensagens](messaging-main/messaging-main.md)
   + Mensagens no aplicativo {#in-app-messaging}
      + [Mensagens no aplicativo](messaging-main/messaging/messaging.md)
      + [Solução de problemas nas mensagens no aplicativo](messaging-main/messaging/in-apps-ts.md)
   + Push messaging {#push-messaging}
      + [Mensagens de push](messaging-main/push-messaging/push-messaging.md)
      + [Implementação de mensagens de push com deep linking](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [Receber notificações por push avançadas](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [Solução de problemas de mensagens de push](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Localização {#location-ios}
   + [Visão geral de localização](location/location.md)
   + [Localização geográfica e pontos de interesse](location/geo-poi.md)
   + [Rastreamento iBeacon](location/ibeacon.md)
+ Target {#target-ios}
   + [Visão geral do Target](target-main/target-main.md)
   + [Métodos do Target](target-main/c-target-methods.md)
   + [Realizar uma busca prévia por conteúdos em oferta no iOS](target-main/c-mob-target-prefetch-ios.md)
   + [Visualização do Target no iOS](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Visão geral da Experience Cloud](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Métodos de serviço de identidade da Adobe Experience Platform](marketing-cloud/mc-methods.md)
   + [Device Co-op da Experience Cloud](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Métodos do Audience Manager](amm/aam-methods.md)
+ Apple TV implementation with tvOS {#apple-tv-implementation-tvos-ios}
   + [Implementação da Apple TV com tvos](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [Adobe Target para TVML/TVJS](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [Métodos TVJS](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS extension implementation {#ios-ext}
   + [Implementação de extensão do iOS](ios-ext/ios-ext.md)
   + [Implementação de extensão independente](ios-ext/c-stand-alone-extension-implementation.md)
+ [Implementação do Apple Watch com watchos 2](apple-watch-implementation-watchkit.md)
+ iOS SDK reference {#sdk-reference-ios}
   + [Referência do SDK do iOS](reference/reference.md)
   + [IDs da Apple](reference/app-ids.md)
   + [Rastreamento de visitantes entre aplicativos e Web móvel](reference/hybrid-app.md)
   + [Versões do dispositivo iOS](reference/device-versions.md)
+ Privacidade e Regulamento Geral sobre a Proteção de Dados{#privacy-gdpr-ios}
   + [Privacidade e Regulamento Geral sobre a Proteção de Dados](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [Recuperar identificadores armazenados](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [Definir o status de opt-up do usuário](c-mob-privacy-gdpr-ios/privacy.md)
+ Plug-in PhoneGap {#phonegap-ios}
   + [Plug-in phonegap](phonegap/phonegap.md)
   + [Métodos de plug-in do phonegap](phonegap/phonegap-methods.md)
