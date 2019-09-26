---
description: É possível gerar links de aquisição com códigos de rastreamento exclusivos no Adobe Mobile Services. Quando um usuário baixa e executa um aplicativo da App Store depois de clicar no link gerado, o SDK coleta e envia automaticamente os dados de aquisição para os Adobe Mobile Services.
keywords: android;biblioteca;móvel;sdk
seo-description: É possível gerar links de aquisição com códigos de rastreamento exclusivos no Adobe Mobile Services. Quando um usuário baixa e executa um aplicativo da App Store depois de clicar no link gerado, o SDK coleta e envia automaticamente os dados de aquisição para os Adobe Mobile Services.
seo-title: Aquisição de aplicativos móveis
solution: Marketing Cloud,Analytics
title: Aquisição de aplicativos móveis
topic: Desenvolvedor e implementação
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Mobile app acquisition {#mobile-app-acquisition}

É possível gerar links de aquisição com códigos de rastreamento exclusivos no Adobe Mobile Services. When a user downloads and runs an app from the App store after clicking on the generated link, the SDK automatically collects and sends the acquisition data to Adobe Mobile services.

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>Para usar o Acquisition, você **deve** ter a versão 4.1 ou posterior do SDK.

Os links de aquisição devem ser criados nos Adobe Mobile Services. For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

**Nas versões 4.13.1 e posteriores do SDK**:

Se você não puder usar os links de aquisição criados no Adobe Mobile Services, os dados de aquisição ainda poderão ser coletados e enviados pelo SDK com o Google Play Acquisition.

Para coletar os dados de aquisição de uma campanha padrão do Google Play Acquisition:

* Use o método de aquisição padrão da Google Play Store.

   Os dados de aquisição personalizados podem ser usados com os pares de valores principais padrão do Google Play Acquisition.

* Quando um usuário baixa e executa um aplicativo como o resultado de uma aquisição da Google Play Store, os dados do referenciador são coletados e enviados para o Adobe Mobile Services.

   * The data is stored and available in the `AdobeDataCallback` instance that was registered earlier with the SDK.

      Para obter mais informações, consulte Métodos [](/help/android/configuration/methods.md)de configuração.

   * Os tipos `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` ou `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` eventos são usados.

   * As chaves personalizadas que faziam parte dos dados de aquisição do Google Play terão "`a.acquisition.custom.`" no nome.

Se você estiver usando os links do Acquisition criados no Adobe Mobile Services, adicione dados personalizados ao link de aquisição quando concluir as seguintes tarefas:

1. Coloque o prefixo "`adb`" em uma variável da aquisição.

   When the SDK receives the acquisition data from Adobe Mobile Services (on first launch), that data will be stored and also available in the `AdobeDataCallback` instance registered earlier with the SDK, as mentioned in [Configuration Methods](/help/android/configuration/methods.md).

1. The `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` or the `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` event type will be used.

1. The custom data keys are prefixed with "`a.acquisition.custom.`"

>[!TIP]
>
>Se você estiver enviando dados para vários conjuntos de relatórios, use os dados de aquisição do aplicativo que está associado ao primeiro conjunto de relatórios na lista de IDs de conjunto de relatórios.

As atualizações nessa seção permitem que o SDK envie dados de aquisição a partir de um link de aquisição.

## Tracking mobile acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. Add the library [to your project and implement lifecycle.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto* IntelliJ IDEA ou Eclipse na implementação e ciclo de vida [principal](/help/android/getting-started/dev-qs.md).

1. Importe a biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Implemente `BroadcastReceiver` para o referenciador:

   ```java
   package com.your.package.name;  // replace with your app package name 
   
   import android.content.BroadcastReceiver; 
   import android.content.Context; 
   import android.content.Intent; 
   
   public class GPBroadcastReceiver extends BroadcastReceiver { 
     @Override 
     public void onReceive(Context c, Intent i) { 
      com.adobe.mobile.Analytics.processReferrer(c, i); 
     } 
   }
   ```

1. Atualize `AndroidManifest.xml` para habilitar `BroadcastReceiver` criado na etapa anterior:

   ```xml
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
    <intent-filter> 
     <action android:name="com.android.vending.INSTALL_REFERRER" /> 
    </intent-filter> 
   </receiver>
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required acquisition settings:

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   > Se estiver enviando dados para vários conjuntos de relatórios, use as configurações de aquisição (servidor de aquisição e appid) do aplicativo associado ao primeiro conjunto de relatórios na sua lista de IDs de conjuntos de relatórios.

   The `acquisition` settings are generated by Adobe Mobile services and should not be changed. For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/android/getting-started/requirements.md).

Quando estas configurações estiverem habilitadas, após a primeira inicialização do aplicativo, os dados de aquisição serão enviados automaticamente com a chamada de ciclo de vida inicial.

>[!CAUTION]
>
>`referrerTimeout` O  deve ser definido com um valor maior que 0 para habilitar a aquisição do aplicativo.
