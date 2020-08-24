---
description: Essas extensões fornecem uma maneira muito mais fácil de adicionar a referência do Experience Cloud Solutions 4.x SDK do Windows no seu projeto.
seo-description: Essas extensões fornecem uma maneira muito mais fácil de adicionar a referência do Experience Cloud Solutions 4.x SDK do Windows no seu projeto.
seo-title: Extensões do Visual Studio do Windows para Experience Cloud Solutions 4.x SDK
solution: Marketing Cloud,Analytics
title: Extensões do Visual Studio do Windows para Experience Cloud Solutions 4.x SDK
topic: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
translation-type: tm+mt
source-git-commit: 38e63d6f4f85c2ced6364baa47646241ac783c12
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Essas extensões fornecem uma maneira muito mais fácil de adicionar a referência do Experience Cloud Solutions 4.x SDK do Windows no seu projeto.

## Instalar a biblioteca do GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Baixe o Windows Universal SDK do [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Descompacte o arquivo baixado localmente.
1. Clique com o duplo no arquivo ADBMobileWindowsStoreVSIX.vsix ou ADBMobileWindowsPhoneVSIX.vsix para abrir o instalador.

1. Selecione Localização **** global e instale a biblioteca.

## Adicionar referências ao seu projeto {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Abra o projeto do Windows 8.1 ou do Windows Phone 8.1.
1. Abra a caixa de diálogo Gerenciador de referência.

   ![](assets/ref_manager.png)

1. Na guia **[!UICONTROL Extensões]** do Windows 8.1 ou Windows Phone 8.1, localize e selecione **[!UICONTROL Adobe Mobile SDK]**.
1. Click **[!UICONTROL OK]** to save it.

   O SDK do Adobe Mobile será adicionado ao seu projeto e, se ele ainda não tiver sido adicionado, o pacote do **[!UICONTROL Microsoft Visual C++ Runtime]** também será adicionado.

1. No Configuration Manager, selecione um tipo de plataforma e comece a testar seu aplicativo.

