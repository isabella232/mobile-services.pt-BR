---
description: Você pode fornecer mensagens no aplicativo que são acionadas a partir de qualquer evento ou dado de análise. Após a implementação, as mensagens são entregues dinamicamente ao aplicativo e não exigem uma atualização de código.
seo-description: Você pode fornecer mensagens no aplicativo que são acionadas a partir de qualquer evento ou dado de análise. Após a implementação, as mensagens são entregues dinamicamente ao aplicativo e não exigem uma atualização de código.
seo-title: Mensagens no aplicativo
solution: Experience Cloud,Analytics
title: Mensagens no aplicativo
topic-fix: Developer and implementation
uuid: 351ee3d2-80b9-4f2d-9696-21f274d89f5a
exl-id: ca9414d1-86e6-4bb2-a2d6-57df37df2403
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 100%

---

# Mensagens no aplicativo {#in-app-messaging}

Você pode fornecer mensagens no aplicativo que são acionadas a partir de qualquer evento ou dado de análise. Após a implementação, as mensagens são entregues dinamicamente ao aplicativo e não exigem uma atualização de código.

## Nova versão do SDK da Adobe Experience Cloud

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para obter a documentação mais recente.

>[!IMPORTANT]
>
>Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o [Launch](https://launch.adobe.com/).
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> Se você estiver usando os SDKs para dispositivos móveis da Adobe Experience Platform com o Adobe Launch, também **deve** instalar a extensão Adobe Analytics Mobile Services para usar os recursos do Adobe Mobile Services, como mensagens no aplicativo e notificações por push. Para obter mais informações, consulte [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Para obter mais informações sobre como usar mensagens por push e mensagens no aplicativo com os SDKs da Experience Cloud, consulte [Configurar mensagens por push](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) e [Configurar mensagens no aplicativo](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>Para usar mensagens no aplicativo, você **deve** ter o SDK versão 4.2 ou posterior.

Você pode criar mensagens e regras no Adobe Mobile Services que definem quando as mensagens são exibidas. Para obter mais informações, consulte [ Criar uma mensagem no aplicativo](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md). Para exibir mensagens no aplicativo, as atualizações devem ser feitas no SDK. Você pode concluir essas etapas mesmo que ainda não tenha definido nenhuma mensagem. Depois de definir as mensagens, elas são entregues de forma dinâmica ao seu aplicativo e exibidas sem uma atualização da loja de aplicativos.

## Ativar mensagens no aplicativo {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto IntelliJ IDEA ou Eclipse* na [Implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Atualize o arquivo `AndroidManifest.xml` para declarar a atividade de tela cheia e ativar o Manipulador de notificação de mensagem:

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

1. Em cada chamada `collectLifecycleData`, use `this` para fornecer uma referência à atividade atual:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
   }
   ```

1. Verifique se o arquivo `ADBMobileConfig.json` contém as configurações exigidas para mensagens no aplicativo.

   >[!IMPORTANT]
   >
   >`messages` ou `remotes` são obrigatórios.

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

   Se esse objeto não estiver configurado, baixe um arquivo `ADBMobileConfig.json` atualizado do Adobe Mobile Services. Para obter mais informações, consulte [Antes de começar](/help/android/getting-started/requirements.md).

## Rastreamento de mensagens no aplicativo {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Os SDKs móveis do Android rastreiam as seguintes métricas para as mensagens no aplicativo:

* Para mensagens no aplicativo com estilo de tela cheia e de alerta:

   * **Impressões**: quando o usuário aciona uma mensagem no aplicativo.
   * **Click-throughs**: quando o usuário pressiona o botão **[!UICONTROL Click-through]**.
   * **Cancelamentos**: quando o usuário pressiona **[!UICONTROL Cancelar]**.

* Para mensagens no aplicativo personalizadas em tela inteira, o conteúdo HTML na mensagem precisa incluir o código correto para notificar ao rastreamento de SDK sobre os seguintes botões:

   * Exemplo de rastreamento de **click-through** (redirecionamento):

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * Exemplo de rastreamento de **cancelamento** (fechar):

      `adbinapp://cancel`

## Imagem de fallback local {#section_DEACC1CE549B4573B556A44A52409941}

Ao criar uma mensagem em tela cheia, você pode especificar uma imagem de fallback. Se a mensagem não puder recuperar a imagem desejada da Web, o SDK tentará carregar a imagem com o mesmo nome da pasta de ativos do aplicativo. Isso permite que você mostre a mensagem em sua forma original, mesmo se o usuário estiver offline ou se a imagem predeterminada estiver inacessível.

>[!IMPORTANT]
>
>O nome do ativo de imagem de fallback é especificado ao configurar a mensagem no Adobe Mobile Services e é necessário assegurar que o recurso especificado esteja disponível.

## Configuração de ícones de notificação {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

Os métodos a seguir permitem configurar os ícones pequeno e grande que aparecem na área de notificações e o ícone grande exibido quando as notificações aparecem na gaveta de notificações.

* **Config.setSmallIconResourceId(int resourceId)**

   Defina o ícone pequeno que será utilizado para notificações criadas pelo SDK. Esse ícone aparecerá na barra de status e será a imagem secundária exibida quando o usuário visualizar a notificação completa na central de notificações.

   * Esta é a sintaxe para este método:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Este é um exemplo de código para este método:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   Define o ícone grande que será utilizado para notificações criadas pelo SDK. Este ícone é a principal imagem exibida quando o usuário visualizar a notificação completa na central de notificações.

   * Esta é a sintaxe para este método:

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```
