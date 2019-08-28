---
description: Estas informações ajudam a usar as mensagens nos aplicativos iOS.
seo-description: Estas informações ajudam a usar as mensagens nos aplicativos iOS.
seo-title: Mensagens no aplicativo
solution: Marketing Cloud, Analytics
title: Mensagens no aplicativo
topic: Desenvolvedor e implementação
uuid: 21 fa 6 a 94-bb 7 f -4 c 78-843 b-a 50 f 1974 db 22
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mensagens no aplicativo {#in-app-messaging}

Estas informações ajudam a usar as mensagens nos aplicativos iOS.

Para usar as mensagens no aplicativo, você **deve** ter o SDK versão 4.2 ou posterior.

Algumas informações para lembrar:

* As mensagens e as regras que definem quando as mensagens são exibidas são criadas nos Adobe Mobile Services. Para obter mais informações, consulte [Criar uma mensagem no aplicativo](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md).
* As atualizações descritas nesta seção devem ser feitas no SDK para exibir mensagens no aplicativo.

   >[!TIP]
   >
   >Você pode concluir essas etapas mesmo que não tenha mensagens definidas. Depois de definir mensagens, elas são entregues dinamicamente ao seu aplicativo e exibidas sem uma atualização da app store.

## Enabling in-app messages {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o Arquivo de configuração ao projeto* na [Implementação principal e no ciclo de vida](/help/ios/getting-started/requirements.md).

1. Importe a biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required settings for In-App messaging.
1. Para que as mensagens no aplicativo sejam atualizadas dinamicamente na inicialização, o objeto `remotes` deve estar presente e configurado corretamente:

   ```js
   “messages”: [ 
       { 
           “messageId”: “de45c43c-37bf-441f-8cbd-cc3ba3469ebe”, 
           “template”: “fullscreen”, 
           “showOffline”: false, 
           “showRule”: “always”, 
           “endDate”: 2524730400, 
           “startDate”: 0, 
           “audiences”: [], 
           “triggers”: [], 
           “payload”: { // contents change depending on template 
               “html”: “<html>html code goes here</html>” 
           }, 
       }, 
       … 
   ] 
   “remotes” : { 
       “analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”, 
       “messages”: “https://assets.adobedtm.com/…/yourfile.json” 
   }
   ```

   >[!TIP]
   >
   >`messages` ou `remotes` é obrigatório.

   If these objects are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Para obter mais informações, consulte [Implementação principal e ciclo de vida](/help/ios/getting-started/requirements.md).

## Tracking in-app messages {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Os SDKs dos iOS Mobile Services rastreiam as seguintes métricas de suas mensagens no aplicativo:

* Para mensagens no aplicativo em tela inteira ou no estilo de alerta:

   * **[!UICONTROL Impressões]**: quando o usuário aciona uma mensagem no aplicativo.
   * **[!UICONTROL Click-throughs: quando o usuário empurra o]** botão Click-through **[!UICONTROL .]**
   * **[!UICONTROL Cancela]**: quando o usuário pressionar o **[!UICONTROL botão Cancelar]** .

* Para mensagens no aplicativo personalizadas em tela inteira, o conteúdo HTML na mensagem precisa incluir o código correto para notificar ao rastreamento de SDK sobre os seguintes botões:

   * **[!UICONTROL Rastreamento de exemplo de click-through]** (redirecionamento): `adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL Cancelar o rastreamento]** de exemplo (fechar): `adbinapp://cancel`

* Em notificações locais (remotas):

   * **[!UICONTROL Impressões]**: quando o usuário aciona a notificação.
   * **[!UICONTROL Abrir]**: quando o usuário abre o aplicativo pela notificação.
   Este é um exemplo de como incluir o rastreamento aberto:

   ```objective-c
   - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
     // handle local notification click-throughs for iOS 10 and older 
     NSDictionary *localNotificationDictionary = launchOptions[UIApplicationLaunchOptionsLocalNotificationKey]; 
     if ([localNotificationDictionary isKindOfClass:[NSDictionary class]]) { 
          [ADBMobile trackLocalNotificationClickThrough:localNotificationDictionary]; 
     } 
   } 
   - (void) application:(UIApplication *)application didReceiveLocalNotification:(UILocalNotification *)notification { 
      [ADBMobile trackLocalNotificationClickThrough:notification.userInfo]; 
   }
   ```

## Local fallback image {#section_DEACC1CE549B4573B556A44A52409941}

Ao criar uma mensagem em tela cheia nos Adobe Mobile Services, você pode opcionalmente especificar uma imagem alternativa. Se a sua mensagem não conseguir recuperar a imagem desejada da Web, o SDK tentará carregar a imagem com o mesmo nome do pacote de aplicativos. Isso permite que você exiba sua mensagem em sua forma original, mesmo que o usuário esteja offline ou a imagem predeterminada esteja inacessível.

O nome do recurso de imagem de retorno é especificado ao configurar a mensagem nos Adobe Mobile Services.

>[!IMPORTANT]
>
>É necessário garantir que o recurso especificado esteja disponível.

