---
description: Estas Extensões fornecem um maneira muito mais fácil de adicionar a referência do Windows SDK 4.x para as soluções da Experience Cloud ao projeto.
seo-description: Estas Extensões fornecem um maneira muito mais fácil de adicionar a referência do Windows SDK 4.x para as soluções da Experience Cloud ao projeto.
seo-title: Extensões do Visual Studio do Windows para o SDK 4.x das Soluções da Experience Cloud
solution: Marketing Cloud,Analytics
title: Extensões do Visual Studio do Windows para o SDK 4.x das Soluções da Experience Cloud
topic: Desenvolvedor e implementação
uuid: e48faf54-8b08-4224-9d80-e553a983129e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

This extension provides a much easier way to add the reference of the Experience Cloud Solutions 4.x Windows SDK in your project.

## Instalar a biblioteca do GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Baixe o SDK universal do Windows a partir do [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Descompacte o arquivo do download localmente.
1. Clique duas vezes no arquivo **[!UICONTRTOL ADBMobileUniversalWindowsVSIX.vsix]** para abrir o instalador.
1. Selecione Localização **** global e instale a biblioteca.

## Add references to your project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Abra o projeto do Windows 10.
1. Abra a caixa de diálogo Gerenciador de referência.

   ![](assets/ref_manager.png)

1. Na guia **[!UICONTROL Extensões]** , localize e selecione **[UICONTROL Adobe Mobile SDK]**.
1. Clique em **[!UICONTROL OK]para salvá-lo.**

   O SDK do Adobe Mobile será adicionado ao seu projeto. Se o pacote **[UICONTROL Microsoft Visual C++ Runtime]** ainda não tiver sido adicionado, este pacote também será adicionado ao seu projeto.

1. No Configuration Manager, selecione um tipo de plataforma e comece a testar seu aplicativo.

