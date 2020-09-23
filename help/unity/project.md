---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Criar o projeto
solution: Experience Cloud
title: Criar o projeto
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 20%

---


# Criar o projeto{#building-your-project}

## iOS

Quando você cria para iOS, um Projeto Xcode é criado. Por padrão, os arquivos `ADBMobileWrapper.mm` e `AdobeMobileLibrary.a` os arquivos estarão no novo grupo Bibliotecas do projeto. Execute as seguintes etapas manuais necessárias para criar seu aplicativo:

1. Adicione o arquivo `ADBMobileConfig.json` ao projeto.

   Certifique-se de que seja um membro da criação dos públicos alvos necessários.

1. Na guia **[!UICONTROL Criar fases]** do projeto, adicione um link às seguintes bibliotecas:

   * `SystemConfiguration.framework`
(Essa biblioteca já pode estar vinculada.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Para usar mensagens de notificação local no aplicativo do SDK, você deve chamar `ADBMobile.EnableLocalNotifications();` pelo método do Start na primeira cena do Unity.

## Android

Quando você cria para Android, o `apk` arquivo já inclui o `ADBMobileConfig.json` arquivo no local correto. Por padrão, o `AndroidManifest.xml` arquivo na sua `/Plugins/Android` pasta também é usado.

Se precisar usar seu próprio arquivo manifest personalizado, as seguintes alterações devem ser adicionadas.

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
