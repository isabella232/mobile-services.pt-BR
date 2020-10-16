---
product: mobile-services
audience: end-user
user-guide-title: Guia do Android do Mobile Services
breadcrumb-title: Guia do Android
translation-type: tm+mt
source-git-commit: 18ef20df0a32741685e35cee98a1adf4a1b823a1
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 99%

---


# Guia do Android do Mobile Services {#android}

+ [Android SDK 4.x para Soluções da Experience Cloud](overview.md)
+ [Notas de versão](rel-notes.md)
+ Introdução {#getting-started-android}
   + [Introdução](getting-started/getting-started.md)
   + [Antes de começar](getting-started/requirements.md)
   + [Implementação principal e ciclo de vida](getting-started/dev-qs.md)
   + [Regras de processamento e dados de contexto](getting-started/proc-rules.md)
   + [Migrar para a biblioteca do Android 4.x](getting-started/migration-v3.md)
+ Configuração {#configuration-android}
   + [Visão geral da configuração](configuration/configuration.md)
   + [Arquivo de configuração ADBMobile JSON](configuration/json-config/json-config.md)
   + [Substituir o caminho de configuração JSON do ADBMobile](configuration/json-config/json-config-remote.md)
   + [Agrupamento de hits](configuration/hit-batching.md)
   + [Métodos de configuração](configuration/methods.md)
+ [Métricas de ciclo de vida](metrics.md)
+ Analytics {#analytics-android}
   + [Visão geral do Analytics](analytics-main/analytics-main.md)
   + [Rastrear estados do aplicativo](analytics-main/states.md)
   + [Rastrear ações do aplicativo](analytics-main/actions.md)
   + [Rastreamento de falhas do aplicativo](analytics-main/crashes.md)
   + [Ações cronometradas](analytics-main/timed-actions.md)
   + [Valor da vida útil do visitante](analytics-main/lifetime-value.md)
   + Variável products {#products-variable}
      + [Variável products](analytics-main/products/products.md)
      + [Variável products com eVars de merchandising e eventos específicos do produto](analytics-main/products/products-variable-evars-events.md)
   + [Serialização de eventos](analytics-main/event-serialization.md)
   + [Análise de vídeo](analytics-main/video-qs.md)
   + Postbacks {#postbacks}
      + [Visão geral de postbacks](analytics-main/postbacks/postbacks.md)
      + [Exemplo de postbacks](analytics-main/postbacks/postback-example.md)
      + [Postbacks de PII](analytics-main/postbacks/c-pii-postbacks.md)
   + [Métodos do Analytics](analytics-main/analytics-methods.md)
+ Aquisição {#acquisition-android}
   + [Visão geral da aquisição](acquisition-main/acquisition-main-android.md)
   + [Aquisição de aplicativos móveis](acquisition-main/acquisition.md)
   + [Métodos de aquisição](acquisition-main/acquisition-methods.md)
   + Rastreamento de deep links {#tracking-deep-links}
      + [Rastreamento de deep links](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Rastreamento de deep links deferidos de terceiros](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [Testar a aquisição de Links de marketing](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Teste da aquisição V3](acquisition-main/t-testing-version-3-acquisition.md)
   + [Teste de aquisição de legado](acquisition-main/t-testing-acquisition.md)
   + [Solução de problemas de teste de aquisição](acquisition-main/troubleshoot-acquisition-testing.md)
+ Mensagens {#messaging-android}
   + [Visão geral das mensagens](messaging-main/messaging-main-android.md)
   + Mensagens no aplicativo {#inapp-messaging}
      + [Mensagens no aplicativo](messaging-main/messaging/messaging.md)
      + [Resolução de problemas de mensagens no aplicativo](messaging-main/messaging/in-apps-ts.md)
   + Mensagens por push {#push-messaging}
      + [Mensagens por push](messaging-main/push-messaging/push-messaging.md)
      + [Implementar mensagens de push com deep linking](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [Receber notificações por push avançadas](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [Solução de problemas de mensagens por push](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Localização {#location}
   + [Visão geral da localização](location/location.md)
   + [Geolocalização e pontos de interesse](location/geo-poi.md)
   + [Rastreamento de sinal](location/beacon.md)
+ Target {#target-android}
   + [Visão geral do Target](target-main/target-main.md)
   + [Configuração do Target](target-main/target.md)
   + [Métodos do Target](target-main/c-target-methods.md)
   + [Usar a busca prévia para encontrar conteúdos em oferta no Android](target-main/c-mob-target-prefetch-android.md)
   + [Visualização do Target no Android](target-main/c-mob-target-preview-android.md)
+ Experience Cloud {#experience-cloud-android}
   + [Visão geral da Experience Cloud](c-marketing-cloud/c-marketing-cloud.md)
   + [Configuração da Experience Cloud ID](c-marketing-cloud/mcvid.md)
   + [Métodos do Adobe Experience Platform Identity Service](c-marketing-cloud/mc-methods.md)
   + [Device Co-op da Experience Cloud](c-marketing-cloud/t-mob-mc-device-coop-android-.md)
+ Audience Manager {#audience-manager-android}
   + [Visão geral do Audience Manager](audience-manager/audience-manager.md)
   + [Configuração do Audience Manager](audience-manager/audiencemgmt.md)
   + [Métodos do Audience Manager](audience-manager/c-audience-manager-methods.md)
+ Wearables {#wearables-android}
   + [Visão geral do Wearables](wearables/wearables.md)
   + [Android Wearables: introdução](wearables/android-wearable.md)
   + [Android Wearables: observações adicionais](wearables/c-android-wearables--additional-notes.md)
+ Referência do Android SDK {#sdk-reference-android}
   + [Visão geral de referência do SDK do Android](/help/android/reference/reference.md)
   + [IDs da Apple](/help/android/reference/app-ids.md)
   + [Rastreamento de visitantes entre um aplicativo e a internet móvel](/help/android/reference/hybrid-app.md)
   + [Widgets do Android](/help/android/reference/widgets.md)
+ Privacidade e Regulamento Geral sobre a Proteção de Dados {#gdpr-privacy-android}
   + [Visão geral sobre privacidade e GDPR](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [Recuperação de identificadores armazenados](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [Definição de status de opção do usuário](c-mob-privacy-gdpr-android/privacy.md)
+ Plug-in PhoneGap {#phonegap-android}
   + [Visão geral do plug-in PhoneGap](phonegap/phonegap.md)
   + [Métodos do plug-in PhoneGap](phonegap/phonegap-methods.md)
