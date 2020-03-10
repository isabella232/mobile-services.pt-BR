---
description: Este plug-in permite o envio de chamadas do Adobe Analytics por meio dos aplicativos Unity.
keywords: Unity
seo-description: Este plug-in permite o envio de chamadas do Adobe Analytics por meio dos aplicativos Unity.
seo-title: Plug-in do Unity para SDKs do iOS e Android 4.x
solution: Marketing Cloud,Developer
title: Plug-in do Unity para SDKs do iOS e Android 4.x
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: tm+mt
source-git-commit: 0d50c7e6674de33b8190e74c113ae010ff226e97

---


# Plug-in do Unity para SDKs do iOS e Android 4.x {#unity-plug-in-for-the-ios-and-android-x-sdks}

Este plug-in permite o envio de chamadas do Adobe Analytics por meio dos aplicativos Unity.

Last Update: **March 10, 2020**
* [Unity-v4.19.0](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases/tag/v4.19.0-Unity)

## Introdução {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Baixe o arquivo ADBMobile.unitypackage do GitHub.

Below are the contents of the `ADBMobile.unitypackage` file:

* Ativos (raiz)

   * ADBMobile

   * Plug-ins

      * ADBMobile.cs
      * Android

         * adobeMobileLibrary-{version}.jar
         * AndroidManifest.xml
         * ativos

            * ADBMobileConfig.json
      * iOS

         * ADBMobile.h
         * ADBMobileConfig.json
         * ADBMobileWrapper.h
         * ADBMobileWrapper.mm
         * AdobeMobileLibrary.a


**Pastas** opcionais: A pasta *Demo* contém cenas do Unity e código de amostra.

## Importação do plug-in ADBMobile para o projeto do Unity {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Abra o seu projeto do Unity.
1. Clique duas vezes em **[!UICONTROL ADBMobile.unitypackage]**.
1. Selecione as pastas que você deseja importar.
