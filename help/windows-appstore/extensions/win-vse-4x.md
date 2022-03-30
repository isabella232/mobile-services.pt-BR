---
description: Essas extensões fornecem uma maneira muito mais fácil de adicionar a referência do Experience Cloud Solutions 4.x Windows SDK no seu projeto.
solution: Experience Cloud Services,Analytics
title: Extensões do Windows Visual Studio para o SDK 4.x das Soluções da Experience Cloud
topic-fix: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
exl-id: 63e9e5c7-2a12-47b3-a712-bf51e12821aa
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 13%

---

# Extensões do Windows Visual Studio para o SDK 4.x das Soluções da Experience Cloud {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Essas extensões fornecem uma maneira muito mais fácil de adicionar a referência do Experience Cloud Solutions 4.x Windows SDK no seu projeto.

## Instalar a biblioteca do GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Baixe o SDK universal do Windows em [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Descompacte o arquivo baixado localmente.
1. Clique duas vezes no arquivo ADBMobileWindowsStoreVSIX.vsix ou ADBMobileWindowsPhoneVSIX.vsix para abrir o instalador.

1. Selecionar **[!UICONTROL Localização Global]** e instale a biblioteca.

## Adicionar referências ao projeto {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Abra o projeto do Windows 8.1 ou do Windows Phone 8.1.
1. Abra a caixa de diálogo Gerenciador de referência .

   ![](assets/ref_manager.png)

1. No **[!UICONTROL Extensões]** guia do Windows 8.1 ou Windows Phone 8.1, localize e selecione **[!UICONTROL Adobe Mobile SDK]**.
1. Clique em **[!UICONTROL OK]** para salvá-lo.

   O SDK do Adobe Mobile será adicionado ao seu projeto e, se ainda não tiver sido adicionado, a variável **[!UICONTROL Tempo de execução do Microsoft Visual C++]** pacote também é adicionado.

1. No Configuration Manager, selecione um tipo de plataforma e comece a testar seu aplicativo.
