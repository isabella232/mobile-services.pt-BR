---
description: Este plug-in permite o envio de chamadas do Adobe Analytics por meio dos aplicativos Unity.
keywords: Unity
seo-description: Este plug-in permite o envio de chamadas do Adobe Analytics por meio dos aplicativos Unity.
seo-title: Plug-in Unity para SDKs 4.x de iOS e de Android
solution: Marketing Cloud,Desenvolvedor
title: Plug-in Unity para SDKs 4.x de iOS e de Android
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: tm+mt
source-git-commit: df4ff7128357a18c56d840eb5697f9c8813ad751

---


# Plug-in Unity para SDKs 4.x de iOS e de Android {#unity-plug-in-for-the-ios-and-android-x-sdks}

Este plug-in permite o envio de chamadas do Adobe Analytics por meio dos aplicativos Unity.

Last Updated: **November 12, 2019**

## Introdução {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Baixe o arquivo [ADBMobile.unitypackage](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) de GitHub ou do Developer Connection.

Estes são os conteúdos do `ADBMobile.unitypackage` arquivo:

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


Pastas opcionais: a pasta Demonstração contém cenas e códigos de amostra do Unity para cada uma das linguagens de script compatíveis.

## Importação do plug-in ADBMobile para o projeto do Unity {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Abra o seu projeto do Unity.
1. Clique duas vezes em **[!UICONTROL ADBMobile.unitypackage]**.
1. Selecione as pastas que você deseja importar.

