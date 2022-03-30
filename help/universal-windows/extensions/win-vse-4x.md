---
description: Essas extensões fornecem uma maneira muito mais fácil de adicionar a referência do Experience Cloud Solutions 4.x Windows SDK no seu projeto.
solution: Experience Cloud Services,Analytics
title: Extensões do Windows Visual Studio para o SDK 4.x das Soluções da Experience Cloud
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 14%

---

# Extensões do Windows Visual Studio para o SDK 4.x das Soluções da Experience Cloud {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Essa extensão oferece uma maneira muito mais fácil de adicionar a referência do Experience Cloud Solutions 4.x Windows SDK no seu projeto.

## Instalar a biblioteca do GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Baixe o SDK universal do Windows em [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Descompacte o arquivo baixado localmente.
1. Clique duas vezes no botão **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** para abrir o instalador.
1. Selecionar **[!UICONTROL Localização Global]** e instale a biblioteca.

## Adicionar referências ao projeto {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Abra o projeto do Windows 10.
1. Abra a caixa de diálogo Gerenciador de referência .

   ![](assets/ref_manager.png)

1. No **[!UICONTROL Extensões]** guia , localize e selecione **[!UICONTROL Adobe Mobile SDK]**.
1. Clique em **[!UICONTROL OK]** para salvá-lo.

   O Adobe Mobile SDK será adicionado ao seu projeto. Se a variável **[!UICONTROL Tempo de execução do Microsoft Visual C++]** ainda não tiver sido adicionado, este pacote também será adicionado ao seu projeto.

1. No Configuration Manager, selecione um tipo de plataforma e comece a testar seu aplicativo.
