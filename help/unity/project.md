---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Construção do projeto
solution: Marketing Cloud,Developer
title: Construção do projeto
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: 0d50c7e6674de33b8190e74c113ae010ff226e97

---


# Building your project{#building-your-project}

## iOS

Ao construir para iOS, um Projeto Xcode é criado. Por padrão, os arquivos `ADBMobileWrapper.mm` e `AdobeMobileLibrary.a` estarão no novo grupo de Bibliotecas do projeto. Execute as seguintes etapas manuais para construir o aplicativo:

1. Adicione o arquivo `ADBMobileConfig.json` ao projeto.

   Certifique-se de que seja um membro da construção de destinos necessários.

1. In the **[!UICONTROL Build Phases]** tab of your project, add a link to the following libraries:

   * `SystemConfiguration.framework`
(Essa biblioteca já pode estar vinculada.)

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

Se você estiver usando mensagens no aplicativo, adicione a seguinte atividade e receptor:

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" />
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```
