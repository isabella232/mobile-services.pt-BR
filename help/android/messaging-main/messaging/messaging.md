---
description: É possível fornecer mensagens no aplicativo disparadas dos dados do Analytics ou de eventos. Depois da implementação, as mensagens são fornecidas dinamicamente ao aplicativo e não necessitam uma atualização de código.
seo-description: É possível fornecer mensagens no aplicativo disparadas dos dados do Analytics ou de eventos. Depois da implementação, as mensagens são fornecidas dinamicamente ao aplicativo e não necessitam uma atualização de código.
seo-title: Mensagens no aplicativo
solution: Marketing Cloud, Analytics
title: Mensagens no aplicativo
topic: Desenvolvedor e implementação
uuid: 351 ee 3 d 2-80 b 9-4 f 2 d -9696-21 f 274 d 89 f 5 a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mensagens no aplicativo {#in-app-messaging}

É possível fornecer mensagens no aplicativo disparadas dos dados do Analytics ou de eventos. Depois da implementação, as mensagens são fornecidas dinamicamente ao aplicativo e não necessitam uma atualização de código.

## Nova versão do SDK da Adobe Experience Cloud

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

>[!IMPORTANT]
>
>Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para começar, acesse o [Launch](https://launch.adobe.com/).
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-app messaging and push notifications. Para obter mais informações, consulte [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). For more information about using push messaging and in-app messaging with the Experience Cloud SDKs, see [Set up push messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) and [Set up in-app messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>Para usar as mensagens no aplicativo, você **deve** ter a versão 4.2 ou posterior do SDK.

É possível criar mensagens e regras no Adobe Mobile Services que definem quando as mensagens são exibidas. Para obter mais informações, consulte [Criar uma mensagem no aplicativo](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md). Para exibir mensagens no aplicativo, devem ser feitas atualizações no SDK. É possível completar essas etapas mesmo que não tenha definido nenhuma mensagem. Depois de definir as mensagens, elas serão entregues dinamicamente ao seu aplicativo e exibidas sem uma atualização da app store.

## Enabling in-app messaging {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o Arquivo de configuração ao projeto intellij IDEA ou Eclipse* na [implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Update the `AndroidManifest.xml` file to declare the full screen activity and enable the Message Notification Handler:

   ```java
   <activity  
   android:name="com.adobe.mobile.MessageFullScreenActivity"  
   android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

   Se selecionar um layout modal (centro da página), selecione um dos temas a seguir para as mensagens:

   * `Theme.Translucent.NoTitleBar.Fullscreen`
   * `Theme.Translucent.NoTitleBar`
   * `Theme.Translucent`
   Por exemplo:

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
   android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. Importe a biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. In each `collectLifecycleData` call, pass `this` to provide a reference to your current activity:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
   }
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required settings for in-app messaging.

   >[!IMPORTANT]
   >
   >`messages` ou `remotes` é obrigatório.

   Para que as mensagens no aplicativo sejam atualizadas dinamicamente, o objeto `remotes` deve ser apresentado e devidamente configurado:

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

   If this object is not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Para obter mais informações, consulte [Antes de começar](/help/android/getting-started/requirements.md).

## Tracking in-app messages {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Os SDKs do Android Mobile rastreiam as seguintes métricas de suas mensagens no aplicativo:

* Para mensagens no aplicativo em tela inteira ou no estilo de alerta:

   * **Impressões**: quando o usuário aciona uma mensagem no aplicativo.
   * **Click-throughs: quando o usuário pressiona****Click through.**
   * **Cancela**: quando o usuário pressiona **[!UICONTROL Cancelar.]**

* Para mensagens no aplicativo personalizadas em tela inteira, o conteúdo HTML na mensagem precisa incluir o código correto para notificar ao rastreamento de SDK sobre os seguintes botões:

   * **Rastreamento de exemplo de click-through** (redirecionamento):

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * **Cancelar o rastreamento** de exemplo (fechar):

      `adbinapp://cancel`

## Local fallback image {#section_DEACC1CE549B4573B556A44A52409941}

Ao criar uma mensagem de tela cheia, é possível especificar uma imagem de fallback. Se a mensagem não consegue recuperar a imagem desejada da Web, o SDK tenta carregar a imagem com o mesmo nome da pasta de ativos do aplicativo. Essa ação permite exibir a mensagem na forma original, mesmo que o usuário esteja offline, ou que a imagem predeterminada não possa ser alcançada.

>[!IMPORTANT]
>
>O nome do ativo de imagem de fallback é especificado quando você configura a mensagem nos Adobe Mobile Services e precisa garantir que o recurso especificado esteja disponível.

## Configuring notification icons {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

Os métodos a seguir permitem configurar os ícones pequeno e grande que aparecem na área de notificações e o ícone grande exibido quando as notificações aparecem na gaveta de notificações.

* **Config.setSmallIconResourceId(int resourceId)**

   Define o ícone pequeno que será utilizado para notificações criadas pelo SDK. Este ícone é exibido na barra de status, e é a imagem secundária exibida quando o usuário visualiza a notificação por completo na central de notificações.

   * Esta é a sintaxe para este método:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Este é o exemplo de código para este método:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   Define o ícone grande que será utilizado para notificações criadas pelo SDK. Este ícone é a principal imagem exibida quando o usuário visualiza a notificação completa na central de notificações.

   * Esta é a sintaxe para este método:

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```
