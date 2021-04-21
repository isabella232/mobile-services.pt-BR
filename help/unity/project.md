---
description: Criação de projetos do iOS
keywords: Unity
solution: Experience Cloud
title: Criar o projeto
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 18%

---

# Criar o projeto{#building-your-project}

## iOS

Ao criar para iOS, um Projeto Xcode é criado. Por padrão, os arquivos `ADBMobileWrapper.mm` e `AdobeMobileLibrary.a` estarão no novo grupo Bibliotecas do projeto. Execute as seguintes etapas manuais necessárias para criar seu aplicativo:

1. Adicione o arquivo `ADBMobileConfig.json` ao projeto.

   Certifique-se de que seja um membro da criação de destinos necessários.

1. Na guia **[!UICONTROL Criar fases]** do projeto, adicione um link às seguintes bibliotecas:

   * `SystemConfiguration.framework`
(Essa biblioteca já pode estar vinculada.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Para usar mensagens de Notificação local no aplicativo do SDK, você deve chamar `ADBMobile.EnableLocalNotifications();` do método Start na primeira Cena do Unity.

## Android

Ao criar para Android, o arquivo `apk` já inclui o arquivo `ADBMobileConfig.json` no local correto. Por padrão, o arquivo `AndroidManifest.xml` em sua pasta `/Plugins/Android` também é usado.

Se precisar usar seu próprio arquivo de manifesto personalizado, as seguintes alterações devem ser adicionadas.

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
