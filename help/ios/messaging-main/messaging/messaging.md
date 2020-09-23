---
description: Estas informações ajudam a usar as mensagens no aplicativo nos aplicativos iOS.
seo-description: Estas informações ajudam a usar as mensagens no aplicativo nos aplicativos iOS.
seo-title: Mensagens no aplicativo
solution: Experience Cloud,Analytics
title: Mensagens no aplicativo
topic: Developer and implementation
uuid: 21fa6a94-bb7f-4c78-843b-a50f1974db22
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 55%

---


# Mensagens no aplicativo {#in-app-messaging}

Estas informações ajudam a usar as mensagens no aplicativo nos aplicativos iOS.

To use in-app messaging, you **must** have SDK version 4.2 or later.

Algumas informações para lembrar:

* As mensagens e as regras que definem quando as mensagens são exibidas são criadas no Adobe Mobile Services. For more information, see [Create an in-app message](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md).
* As atualizações descritas nesta seção devem ser feitas no SDK para exibir mensagens no aplicativo.

   >[!TIP]
   >
   >É possível concluir essas etapas, mesmo que não tenha mensagens definidas. Depois de definir as mensagens, elas são entregues de forma dinâmica ao seu aplicativo e exibidas sem atualização da loja de aplicativos.

## Ativar mensagens no aplicativo {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao seu projeto* em [Implementação principal e ciclo de vida](/help/ios/getting-started/requirements.md).

1. Importe a biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verifique se o arquivo `ADBMobileConfig.json` contém as configurações exigidas para mensagens no aplicativo.
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
   >`messages` ou `remotes` são obrigatórios.

   Se esses objetos não estiverem configurados, baixe um arquivo `ADBMobileConfig.json` atualizado do Adobe Mobile Services. Para obter mais informações, consulte [Implementação principal e ciclo de vida](/help/ios/getting-started/requirements.md).

## Rastreamento de mensagens no aplicativo {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Os SDKs do iOS Mobile Services rastreiam as seguintes métricas para as mensagens no aplicativo:

* Para mensagens no aplicativo com estilo de tela cheia e de alerta:

   * **[!UICONTROL Impressões]**: quando o usuário aciona uma mensagem no aplicativo.
   * **[!UICONTROL Click-throughs]**: quando o usuário pressiona o botão **[!UICONTROL Click-through]**.
   * **[!UICONTROL Cancelamentos]**: quando o usuário pressiona o botão **[!UICONTROL Cancelar]**.

* Para mensagens no aplicativo personalizadas em tela inteira, o conteúdo HTML na mensagem precisa incluir o código correto para notificar ao rastreamento de SDK sobre os seguintes botões:

   * Exemplo de rastreamento de **[!UICONTROL click-through]** (redirecionamento): `adbinapp://confirm/?url=https://www.yoursite.com`
   * Exemplo de rastreamento de **[!UICONTROL cancelamento]** (fechar): `adbinapp://cancel`

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

## Imagem de fallback local {#section_DEACC1CE549B4573B556A44A52409941}

Ao criar uma mensagem de tela cheia nos Adobe Mobile Services, você pode especificar uma imagem de fallback. Se a mensagem não conseguir recuperar a imagem desejada da Web, o SDK tentará carregar a imagem com o mesmo nome do pacote de aplicativos. Isso permite que você exiba sua mensagem em sua forma original, mesmo se o usuário estiver offline ou se a imagem predeterminada for inacessível.

O nome do ativo de imagem de fallback é especificado ao configurar a mensagem nos Adobe Mobile Services.

>[!IMPORTANT]
>
>É necessário garantir que o recurso especificado esteja disponível.

