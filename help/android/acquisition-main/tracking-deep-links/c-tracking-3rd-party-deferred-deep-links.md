---
description: Use o Android SDK para implementar o rastreamento de deep links adiados de terceiros.
seo-description: Use o Android SDK para implementar o rastreamento de deep links adiados de terceiros.
seo-title: Rastreamento de deep links deferidos de terceiros
title: Rastreamento de deep links deferidos de terceiros
uuid: 4c798e47-7988-4a06-a191-6c4d05f6ee61
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Rastreamento de deep links adiados de terceiros{#tracking-third-party-deferred-deep-links}

Use o Android SDK para implementar o rastreamento de deep links adiados de terceiros.

## Deep linking clássico do Adobe Mobile SDK {#section_D114FA1EB9664EAA82E036A990694B26}

O Adobe Mobile SDK atualmente oferece suporte a deep linking em que o desenvolvedor do aplicativo deve usar a API do SDK `collectLifecycleData` a partir da atividade que sofreu deep linking. O SDK anexa os dados de deep link nos parâmetros de URL do deep link. Para obter mais informações sobre como o deep linking funciona no Adobe Mobile SDK, consulte [Rastreamento de deep links](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Deep linking do Facebook {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Um criador de anúncios pode criar um anúncio no Facebook como um deep link. Quando os usuários clicam no anúncio, ele os direciona diretamente para a informação em que estão interessados no aplicativo. O deep link **não** é um URL de impressão digital. No entanto, durante a configuração do anúncio, existe uma opção para fornecer um URL de deep link de terceiros. Um desenvolvedor de aplicativos que esteja usando os SDKs e o Adobe Mobile Services deve inserir o URL de impressão digital configurado no Adobe Mobile Service neste campo. Se tudo estiver configurado corretamente, o SDK do Facebook transmite esse URL para o aplicativo quando ele for instalado ou iniciado.

## Configuração dos SDKs {#section_834CD3109175432B8173ECB6EA7DE315}

Para preparar a adição do suporte ao deep linking do Facebook com o Adobe Mobile SDK, o desenvolvedor do aplicativo conclui as seguintes tarefas:

* Introdução ao Android SDK

   Para obter mais informações, consulte [Introdução ao Android SDK](https://developers.facebook.com/docs/android/getting-started).

* Configurar deep linking

   Para obter mais informações, consulte [Configurar Deep Linking](https://developers.facebook.com/docs/app-ads/deep-linking#os).

Se o aplicativo estiver configurado corretamente, a API `trackAdobeDeepLink()` deverá habilitar a coleta de informações de deep link da campanha de aquisição do Facebook e enviá-las para o Adobe Mobile Service. Se a ocorrência de instalação não tiver sido enviada para o Adobe Mobile Service na primeira inicialização, essas informações serão adicionadas à ocorrência do ciclo de vida. Caso contrário, serão enviadas como uma ocorrência de deep link da Adobe.

>[!TIP]
>
>Certifique-se de que o URL do deep link tenha uma chave com o nome `a.deeplink.id`. Se o parâmetro de ID do deep link não estiver no URL, os parâmetros de URL não serão anexados aos dados do contexto.

Se o link pode ser atribuído a uma aquisição, o Adobe Mobile SDK armazenará os dados de aquisição do deep link do Facebook usado para chamar `trackAdobeDeepLink()`. Esses dados estarão disponíveis no Adobe Mobile SDK em inicializações futuras. Se uma chamada de retorno for registrada, a chamada de retorno da Adobe também será usada para enviar os dados de volta para o cliente.

## Habilitar deep linking em um aplicativo Android {#section_64C15E269E89424B8E3D029F88094620}

1. Registre o aplicativo para gerenciar os deep links.

   Para obter mais informações, consulte [Permitir que outros aplicativos iniciem a atividade](https://developer.android.com/training/basics/intents/filters.html).

1. Vincule os SDKs do Facebook.

   Para adicionar a dependência de gradle do Facebook no aplicativo, complete as etapas da [Introdução ao Android SDK](https://developers.facebook.com/docs/android/getting-started).

1. Para iniciar o SDK do Facebook, complete as instruções na seção *Configuração do Android Studio*.
1. Faça uma chamada `trackAdobeDeepLink()` a partir da atividade principal.

   ```java
   @Override 
   protected void onResume() { 
      super.onResume(); 
      AppEventsLogger.activateApp(this); 
      /* 
       * Adobe Tracking - Config 
       * 
       * call collectLifecycleData() to begin collecting lifecycle data 
       * must be in the onResume() of every activity in your app 
       */ 
      Config.collectLifecycleData(this);
   
      AppLinkData.fetchDeferredAppLinkData(this, 
            new AppLinkData.CompletionHandler() { 
               @Override 
               public void onDeferredAppLinkDataFetched(AppLinkData appLinkData) { 
                  // Process app link data 
                  if (appLinkData != null) { 
                     Config.trackAdobeDeepLink(appLinkData.getTargetUri()); 
                  } 
               } 
            } 
      ); 
   }
   ```

