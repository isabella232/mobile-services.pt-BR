---
description: Este tópico descreve a introdução aos componentes do Xamarin para os SDK 4.x das soluções do Mobile.
keywords: Xamarin
seo-description: Este tópico descreve a introdução aos componentes do Xamarin para os SDK 4.x das soluções do Mobile.
seo-title: Componentes do Xamarin para SDK Solutions. x das Soluções da Experience Cloud
solution: Marketing Cloud, desenvolvedor
title: Componentes do Xamarin para SDK Solutions. x das Soluções da Experience Cloud
uuid: e 7 a 48107-bd 0 e -47 d 6-b 49 c-dfdae 189 ac 37
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

Este tópico descreve a introdução aos componentes do Xamarin para os SDK 4.x das soluções do Mobile.

Última atualização: **10 de janeiro de 2019**

## Introdução {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>O Adobe Mobile SDK não está mais disponível na Loja de componentes do Xamarin nem na Galeria de nuget. Para baixar os componentes Xamarin, acesse o [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).


## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Importe o componente adbmobile para o projeto Xamarin. Android:

1. Abra o projeto Xamarin

1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Selecione `ADBMobile.XamarinAndroidBinding.dll` a partir da **[!UICONTROL pasta lib/Android]** .

1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.

1. Adicionar permissões para:

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`

   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. Se estiver usando mensagens no aplicativo, adicione a seguinte atividade e receptor:

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar" />
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. Se você estiver usando a aquisição, adicione o seguinte receptor:

   ```java
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
   <intent-filter>
       <action android:name="com.android.vending.INSTALL_REFERRER" />
   </intent-filter>
   </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

Importe o componente adbmobile para o projeto Xamarin. iOS:

1. Abra o projeto Xamarin.
1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Selecione `ADBMobile.XamarinIOSBinding.dll` a partir da **[!UICONTROL pasta lib/ios-unified]** .

1. Adicione o arquivo `ADBMobileConfig.json` ao projeto.


