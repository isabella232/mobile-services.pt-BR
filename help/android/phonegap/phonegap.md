---
description: Este plug-in permite enviar chamadas do Android AppMeasurement a partir do seu projeto PhoneGap.
keywords: android;biblioteca;móvel;sdk
solution: Experience Cloud Services,Analytics
title: Visão geral do plug-in PhoneGap
topic-fix: Developer and implementation
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
exl-id: ecd756ca-e333-4d28-bd1e-a75ffc6ebe22
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 97%

---

# Visão geral do plug-in PhoneGap {#phonegap-plug-in}

Este plug-in permite enviar chamadas do Android AppMeasurement a partir do seu projeto PhoneGap. Para criar um projeto PhoneGap, consulte [PhoneGap](https://helpx.adobe.com/br/experience-manager/6-4/mobile/using/phonegap.html).

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para obter a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Instalar o plug-in usando npm {#section_43229E57C16944C0B51531CB92089189}

Execute o seguinte comando:

```java
cordova plugin add adobe-mobile-services
```

## Instalar o plug-in manualmente  {#section_EA1FD59C484D44878AB509954DEE6037}

## Incluir o plug-in

1. Arraste o arquivo `ADBMobile_PhoneGap.java` para a sua pasta `src`.

   Para mover esse arquivo, clique em **[!UICONTROL OK]**.

1. Arraste o arquivo `ADB_Helper.js` para a pasta que contém o arquivo `index.html`

   Para mover esse arquivo, clique em **[!UICONTROL OK]**.

1. Na pasta `res/xml`, abra `config.xml` e registre um novo plug-in, adicionando o seguinte:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   Por exemplo, se o nome do seu pacote for `com.example.phonegaptest`, o valor `android-package` será o seguinte:

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## Incluir a biblioteca do AppMeasurement

1. Para baixar a biblioteca do AppMeasurement, consulte [Baixar o SDK](/help/android/getting-started/dev-qs.md).
1. Arraste o arquivo `adobeMobileLibrary.jar` para a sua pasta `src`.

   Para mover esse arquivo, clique em **[!UICONTROL OK]**.

1. Clique com o botão direito do mouse no `adobeMobileLibrary.jar` e selecione **[!UICONTROL Adicionar como biblioteca]**.
1. Com base nas solicitações do projeto, insira o nome, nível e localização da biblioteca.
1. Arraste o arquivo `ADBMobileConfig.json` até a pasta `assets` no aplicativo raiz.
1. Confirme que selecionou o aplicativo raiz e **não** um aplicativo em um aplicativo.

   Para mover esse arquivo, clique em **[!UICONTROL OK]**.

## Adicionar permissões do aplicativo

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

## Implementar o rastreamento personalizado {#section_FD102B3CDAA4492FB04E56BF17E28663}

Nos arquivos `html`, adicione o seguinte código à tag `<head>` em que você deseja usar o rastreamento:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```
