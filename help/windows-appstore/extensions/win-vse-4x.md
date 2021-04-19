---
description: Essas extensões fornecem uma maneira muito mais fácil de adicionar a referência do Experience Cloud Solutions 4.x Windows SDK no seu projeto.
seo-description: Essas extensões fornecem uma maneira muito mais fácil de adicionar a referência do Experience Cloud Solutions 4.x Windows SDK no seu projeto.
seo-title: Extensões do Windows Visual Studio para o SDK 4.x das Soluções da Experience Cloud
solution: Experience Cloud,Analytics
title: Extensões do Windows Visual Studio para o SDK 4.x das Soluções da Experience Cloud
topic-fix: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
exl-id: 63e9e5c7-2a12-47b3-a712-bf51e12821aa
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 16%

---

# Extensões do Windows Visual Studio para o SDK 4.x das Soluções da Experience Cloud {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Essas extensões fornecem uma maneira muito mais fácil de adicionar a referência do Experience Cloud Solutions 4.x Windows SDK no seu projeto.

## Instalar a biblioteca do GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Baixe o SDK universal do Windows em [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Descompacte o arquivo baixado localmente.
1. Clique duas vezes no arquivo ADBMobileWindowsStoreVSIX.vsix ou ADBMobileWindowsPhoneVSIX.vsix para abrir o instalador.

1. Selecione **[!UICONTROL Localização Global]** e instale a biblioteca.

## Adicionar referências ao seu projeto {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Abra o projeto do Windows 8.1 ou do Windows Phone 8.1.
1. Abra a caixa de diálogo Gerenciador de referência .

   ![](assets/ref_manager.png)

1. Na guia **[!UICONTROL Extensões]** do Windows 8.1 ou do Windows Phone 8.1, localize e selecione **[!UICONTROL Adobe Mobile SDK]**.
1. Clique em **[!UICONTROL OK]** para salvá-lo.

   O SDK do Adobe Mobile será adicionado ao seu projeto e, se ainda não tiver sido adicionado, o pacote **[!UICONTROL Microsoft Visual C++ Runtime]** também será adicionado.

1. No Configuration Manager, selecione um tipo de plataforma e comece a testar seu aplicativo.
