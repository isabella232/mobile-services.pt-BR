---
description: Este tópico descreve como começar a usar os componentes Xamarin para o SDK 4.x das soluções móveis.
keywords: Xamarin
seo-description: Este tópico descreve como começar a usar os componentes Xamarin para o SDK 4.x das soluções móveis.
seo-title: Componentes Xamarin para Experience Cloud Solutions 4.x SDK
solution: Marketing Cloud,Developer
title: Componentes Xamarin para Experience Cloud Solutions 4.x SDK
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 5%

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

Este tópico descreve como começar a usar os componentes Xamarin para o SDK 4.x das soluções móveis.

Last Updated: **January 10, 2019**

## Introdução {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>O Adobe Mobile SDK não está mais disponível na Loja de componentes do Xamarin ou na Galeria do NuGet. Para baixar os componentes do Xamarin, vá para [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Importe o componente ADBMobile para seu projeto Xamarin.Android:

1. Abra seu projeto Xamarin
1. Abra a caixa de diálogo **[!UICONTROL Referências]** e clique na guia Assembly **** .Net.
1. Selecione `ADBMobile.XamarinAndroidBinding.dll` na pasta **[!UICONTROL lib/Android]** .
1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.
1. Adicionar permissões para:

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`

   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. Se você estiver usando mensagens no aplicativo, adicione a seguinte atividade e receptor:

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

Importe o componente ADBMobile para seu projeto Xamarin.iOS:

1. Abra seu projeto Xamarin.
1. Abra a caixa de diálogo **[!UICONTROL Referências]** e clique na guia Assembly **** .Net.
1. Selecione `ADBMobile.XamarinIOSBinding.dll` na pasta **[!UICONTROL lib/ios-unified]** .
1. Adicione seu `ADBMobileConfig.json` arquivo ao projeto.
