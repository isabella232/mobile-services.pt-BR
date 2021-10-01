---
description: Este tópico descreve como começar a usar os componentes do Xamarin para o SDK 4.x de soluções móveis.
keywords: Xamarin
solution: Experience Cloud
title: Componentes do Xamarin para o SDK 4.x das soluções da Experience Cloud
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
exl-id: 39628548-5787-4022-8792-86b78214a1c0
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 99%

---

# Componentes do Xamarin para o SDK 4.x das soluções da Experience Cloud {#xamarin-components-for-experience-cloud-solutions-x-sdk}

Este tópico descreve como começar a usar os componentes do Xamarin para o SDK 4.x de soluções móveis.

Última atualização: **10 de janeiro de 2019**

## Introdução {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>O SDK móvel da Adobe não está mais disponível na Loja de componentes do Xamarin ou na Galeria do NuGet. Para baixar os componentes do Xamarin, acesse [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Importe o componente ADBMobile para seu projeto Xamarin.Android:

1. Abra o projeto do Xamarin
1. Abra a caixa de diálogo **[!UICONTROL Referências]** e clique na guia **[!UICONTROL .Net Assembly]**.
1. Selecione `ADBMobile.XamarinAndroidBinding.dll` na pasta **[!UICONTROL lib/Android]**.
1. Adicione o arquivo `ADBMobileConfig.json` à pasta **[!UICONTROL Assets]** do projeto.
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

1. Se você estiver usando aquisição, adicione o seguinte receptor:

   ```java
    <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
        <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
    </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

Importe o componente ADBMobile para o projeto Xamarin.iOS:

1. Abra o projeto do Xamarin.
1. Abra a caixa de diálogo **[!UICONTROL Referências]** e clique na guia **[!UICONTROL .Net Assembly]**.
1. Selecione `ADBMobile.XamarinIOSBinding.dll` na pasta **[!UICONTROL lib/ios-unified]**.
1. Adicione o arquivo `ADBMobileConfig.json` ao projeto.
