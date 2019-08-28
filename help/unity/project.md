---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Criação de seu projeto
solution: Marketing Cloud, desenvolvedor
title: Criação de seu projeto
uuid: 5550 a 394-6 f 3 f -4 b 87-b 840-89621 d 8 a 0 c 1 e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Building your project{#building-your-project}

## iOS

Ao construir para iOS, um Projeto Xcode é criado. Por padrão, os arquivos `ADBMobileWrapper.mm` e `AdobeMobileLibrary.a` estarão no novo grupo de Bibliotecas do projeto. Execute as seguintes etapas manuais para construir o aplicativo:

1. Adicione o arquivo `ADBMobileConfig.json` ao projeto.

   Certifique-se de que seja um membro da construção de destinos necessários.

1. In the **[!UICONTROL Build Phases]** tab of your project, add a link to the following libraries:

   * `SystemConfiguration.framework`(Esta biblioteca já pode estar vinculada.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>To use Local Notification In-App messages from the SDK, you must call `ADBMobile.EnableLocalNotifications();` from the Start method in your first Unity Scene.

## Android

Ao construir para Android, o arquivo `apk` já inclui o arquivo `ADBMobileConfig.json` no local correto. By default, the `AndroidManifest.xml` file in your `/Plugins/Android` folder is also used.

Se precisar utilizar um arquivo de manifesto personalizado, é necessário adicionar as seguintes alterações.

Adicionar permissões para:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Se estiver usando mensagens no aplicativo, adicione a seguinte atividade e receptor:

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" /> 
```

Se você estiver usando a aquisição, adicione o seguinte receptor:

```java
<receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
   <intent-filter> 
      <action android:name="com.android.vending.INSTALL_REFERRER" /> 
   </intent-filter> 
</receiver>
```
