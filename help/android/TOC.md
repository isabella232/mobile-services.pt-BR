---
product: mobile-services
audience: usuário final
user-guide-title: Ajuda do Mobile Services Android
translation-type: tm+mt
source-git-commit: e3bbde6c27d583ff3ee8b7e86c8e6e73595f5067

---


# Mobile Services Android Help{#android}

+ [Android SDK 4.x para Soluções da Experience Cloud](overview.md)
+ [Notas de versão](rel-notes.md)
+ Introdução{#getting-started-android}
   + [Introdução](getting-started/getting-started.md)
   + [Before you start](getting-started/requirements.md)
   + [Implementação principal e ciclo de vida](getting-started/dev-qs.md)
   + [Regras de processamento e dados de contexto](getting-started/proc-rules.md)
   + [Migrar para a biblioteca do Android 4.x](getting-started/migration-v3.md)
+ Configuração{#configuration-android}
   + [Configuration overview](configuration/configuration.md)
   + [Arquivo de configuração ADBMobile JSON](configuration/json-config/json-config.md)
   + [Substituir o caminho de configuração ADBMobile JSON](configuration/json-config/json-config-remote.md)
   + [Agrupamento de hits](configuration/hit-batching.md)
   + [Métodos de configuração](configuration/methods.md)
+ [Medições de ciclo de vida](metrics.md)
+ Analytics{#analytics-android}
   + [Visão geral do Analytics](analytics-main/analytics-main.md)
   + [Rastrear estados do aplicativo](analytics-main/states.md)
   + [Rastrear ações do aplicativo](analytics-main/actions.md)
   + [Rastreamento de falhas do aplicativo](analytics-main/crashes.md)
   + [Ações programadas](analytics-main/timed-actions.md)
   + [Valor vitalício do visitante](analytics-main/lifetime-value.md)
   + Products variable{#products-variable}
      + [Variável products](analytics-main/products/products.md)
      + [Variável products com eVars de comercialização e eventos específicos do produto](analytics-main/products/products-variable-evars-events.md)
   + [Serialização de eventos](analytics-main/event-serialization.md)
   + [Análise de vídeo](analytics-main/video-qs.md)
   + Postbacks{#postbacks}
      + [Visão geral de postbacks](analytics-main/postbacks/postbacks.md)
      + [Exemplo de postbacks](analytics-main/postbacks/postback-example.md)
      + [Postbacks de PII](analytics-main/postbacks/c-pii-postbacks.md)
   + [Métodos do Analytics](analytics-main/analytics-methods.md)
+ Aquisição{#acquisition-android}
   + [Visão geral da aquisição](acquisition-main/acquisition-main-android.md)
   + [Aquisição de aplicativos móveis](acquisition-main/acquisition.md)
   + [Métodos de aquisição](acquisition-main/acquisition-methods.md)
   + Tracking deep links{#tracking-deep-links}
      + [Rastrear links profundos](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Rastrear deep links adiados de terceiros](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [Testing Marketing Link acquisition](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Teste da aquisição V3](acquisition-main/t-testing-version-3-acquisition.md)
   + [Teste da aquisição herdada](acquisition-main/t-testing-acquisition.md)
   + [Solução de problemas de teste de aquisição](acquisition-main/troubleshoot-acquisition-testing.md)
+ Mensagens{#messaging-android}
   + [Visão geral das mensagens](messaging-main/messaging-main-android.md)
   + Mensagens no aplicativo{#inapp-messaging}
      + [Mensagens no aplicativo](messaging-main/messaging/messaging.md)
      + [Solução de problemas de mensagens no aplicativo](messaging-main/messaging/in-apps-ts.md)
   + Push messaging{#push-messaging}
      + [Mensagens de push](messaging-main/push-messaging/push-messaging.md)
      + [Implementação de mensagens de push com deep linking](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [Receber notificações por push avançadas](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [Solução de problemas de mensagens de push](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Localização{#location}
   + [Visão geral do local](location/location.md)
   + [Geo-location and points of interest](location/geo-poi.md)
   + [Rastreamento de sinal](location/beacon.md)
+ Target{#target-android}
   + [Visão geral do Target](target-main/target-main.md)
   + [Configuração do Target](target-main/target.md)
   + [Métodos do Target](target-main/c-target-methods.md)
   + [Usar a busca prévia para encontrar conteúdos em oferta no Android](target-main/c-mob-target-prefetch-android.md)
   + [Visualização do Target no Android](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Visão geral da Experience Cloud](c-marketing-cloud/c-marketing-cloud.md)
   + [Experience Cloud ID configuration](c-marketing-cloud/mcvid.md)
   + [Métodos do Adobe Experience Platform Identity Service](c-marketing-cloud/mc-methods.md)
   + [Device Co-op da Experience Cloud](c-marketing-cloud/t-mob-mc-device-coop-android-.md)
+ Audience Manager{#audience-manager-android}
   + [Visão geral do Audience Manager](audience-manager/audience-manager.md)
   + [Audience Manager configuration](audience-manager/audiencemgmt.md)
   + [Métodos do Audience Manager](audience-manager/c-audience-manager-methods.md)
+ Wearables{#wearables-android}
   + [Visão geral do Wearables](wearables/wearables.md)
   + [Android Wearables: introdução](wearables/android-wearable.md)
   + [Android Wearables: additional notes](wearables/c-android-wearables--additional-notes.md)
+ Android SDK reference{#sdk-reference-android}
   + [Visão geral de referência do SDK do Android](/help/android/reference/reference.md)
   + [IDs da Apple](/help/android/reference/app-ids.md)
   + [Rastreamento de visitante entre um aplicativo e a Web móvel](/help/android/reference/hybrid-app.md)
   + [Android widgets](/help/android/reference/widgets.md)
+ Privacidade e Regulamento Geral sobre a Proteção de Dados{#gdpr-privacy-android}
   + [Visão geral sobre privacidade e RGPD](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [Recuperando identificadores armazenados](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [Definir o status de opção do usuário](c-mob-privacy-gdpr-android/privacy.md)
+ Plug-in PhoneGap{#phonegap-android}
   + [Visão geral do plug-in PhoneGap](phonegap/phonegap.md)
   + [Métodos do plug-in PhoneGap](phonegap/phonegap-methods.md)
