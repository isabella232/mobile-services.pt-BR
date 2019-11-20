---
description: Este plug-in permite o envio de chamadas do Adobe Analytics por meio dos aplicativos Unity.
keywords: Unity
seo-description: Este plug-in permite o envio de chamadas do Adobe Analytics por meio dos aplicativos Unity.
seo-title: Plug-in do Unity para SDKs do iOS e Android 4.x
solution: Experience Cloud,Desenvolvedor
title: Plug-in do Unity para SDKs do iOS e Android 4.x
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: ht
source-git-commit: df4ff7128357a18c56d840eb5697f9c8813ad751

---


# Plug-in do Unity para SDKs do iOS e Android 4.x {#unity-plug-in-for-the-ios-and-android-x-sdks}

Este plug-in permite o envio de chamadas do Adobe Analytics por meio dos aplicativos Unity.

Última atualização: **12 de novembro de 2019**

## Introdução {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Baixe o arquivo [ADBMobile.unitypackage](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) do GitHub ou do Developer Connection.

Aqui está o conteúdo do `ADBMobile.unitypackage` arquivo:

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

