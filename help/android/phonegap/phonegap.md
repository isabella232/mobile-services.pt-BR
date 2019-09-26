---
description: Este plug-in permite enviar chamadas do Android AppMeasurement a partir do seu projeto PhoneGap.
keywords: android;biblioteca;móvel;sdk
seo-description: Este plug-in permite enviar chamadas do Android AppMeasurement a partir do seu projeto PhoneGap.
seo-title: Visão geral do plug-in PhoneGap
solution: Marketing Cloud,Analytics
title: Visão geral do plug-in PhoneGap
topic: Desenvolvedor e implementação
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Visão geral do plug-in PhoneGap {#phonegap-plug-in}

Este plug-in permite enviar chamadas do Android AppMeasurement a partir do seu projeto PhoneGap. Para criar um projeto PhoneGap, consulte [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## Nova versão do SDK da Adobe Experience Cloud

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

>[!IMPORTANT]
>
>Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para começar, acesse o [Launch](https://launch.adobe.com/).
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Instalar o plug-in usando npm {#section_43229E57C16944C0B51531CB92089189}

Execute o seguinte comando:

```java
cordova plugin add adobe-mobile-services
```

## Instalar o plug-in manualmente {#section_EA1FD59C484D44878AB509954DEE6037}

## Incluir o plug-in

1. Arraste o `ADBMobile_PhoneGap.java` arquivo para a sua `src` pasta.

   Para mover esse arquivo, clique em **[!UICONTROL OK]**.

1. Arraste o `ADB_Helper.js` arquivo para a pasta que contém o `index.html` arquivo

   Para mover esse arquivo, clique em **[!UICONTROL OK]**.

1. In the `res/xml` folder, open the `config.xml` file and register an new plugin by adding the following:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   Por exemplo, se o nome do seu pacote for `com.example.phonegaptest`, o valor `android-package` será o seguinte:

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## Include the AppMeasurement library

1. To download the AppMeasurement library, see [Get the SDK](/help/android/getting-started/dev-qs.md).
1. Arraste o arquivo para a `adobeMobileLibrary.jar` sua `src` pasta.

   Para mover esse arquivo, clique em **[!UICONTROL OK]**.

1. Right-click the `adobeMobileLibrary.jar file and select **[!UICONTROL Add as Library]**.
1. Com base nas solicitações do projeto, insira o nome, nível e localização da biblioteca.
1. Drag the `ADBMobileConfig.json` file to your `assets` folder in the application root.
1. Confirme que selecionou o aplicativo raiz e **não** um aplicativo em um aplicativo.

   Para mover esse arquivo, clique em **[!UICONTROL OK]**.

## Adicionar permissões de aplicativo

A biblioteca do AppMeasurement pede as seguintes permissões para enviar dados e gravar chamadas de rastreamento offline:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Para adicionar essas permissões, adicione as seguintes linhas no arquivo `AndroidManifest.xml`, localizado no diretório do projeto do aplicativo:

```xml
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Para ativar mensagens no aplicativo:

Atualize o AndroidManifest.xml para declarar a atividade de tela cheia e ativar o Manipulador de notificação de mensagem:

```java
<activity  
android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

Se selecionar o layout modal ao criar uma mensagem no Adobe Mobile Services, selecione um dos seguintes temas:

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

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files, add the following to the `<head>` tag where you want to use tracking:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

