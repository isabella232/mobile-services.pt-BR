---
title: Start rápido do desenvolvedor
seo-title: Start rápido para desenvolvedores BlackBerry para Adobe Mobile Services
description: O Guia de Start Rápido para Desenvolvedores do BlackBerry ajuda você a entender o processo de implementação da biblioteca do BlackBerry para o Adobe Mobile Services.
seo-description: O Guia de Start Rápido para Desenvolvedores do BlackBerry ajuda você a entender o processo de implementação da biblioteca do BlackBerry para o Adobe Mobile Services.
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 1%

---


# Início rápido do desenvolvedor

Essas informações ajudam você a entender o processo de implementação da biblioteca do BlackBerry.

## Obter o SDK

**O SDK exige o BlackBerry 10 ou posterior.**

Após descompactar o SDK baixado, verifique se os seguintes arquivos existem em uma `AdobeMobile` pasta:

* `Device-Coverage/libADBMobileShared.so`
* `Device-Debug/libADBMobileShared.so`
* `Device-Profile/libADBMobileShared.so`
* `Device-Release/libADBMobileShared.so`
* `public/ADBMediaAnalytics.hpp`
* `public/ADBMediaSharedHeader.hpp`
* `public/ADBMediaState.hpp`
* `public/ADBMobile.hpp`
* `Simulator-Coverage/libADBMobileShared.so`
* `Simulator-Debug/libADBMobileShared.so`
* `Simulator-Profile/libADBMobileShared.so`

## Adicionar os SDKs ao seu projeto

1. Clique com o botão direito do mouse em seu projeto e selecione **[!UICONTROL Configurar]** > **[!UICONTROL Adicionar biblioteca]**.
1. Selecione Biblioteca **** externa e clique em **[!UICONTROL Avançar]**.
1. Clique em **[!UICONTROL Procurar]** ao lado do campo Biblioteca **[!UICONTROL de]** dispositivos.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Na `Device-Debug` pasta, selecione `libADBMobileShared.so` e clique em **[!UICONTROL Abrir]**.
1. Clique em **[!UICONTROL Procurar]** ao lado do campo Biblioteca **[!UICONTROL do]** simulador.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Na `Device-Debug` pasta, selecione `libADBMobileShared.so` e clique em **[!UICONTROL Abrir]**.
1. Clique em **[!UICONTROL Adicionar]** ao lado do campo **[!UICONTROL Incluir pastas]** .
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Adicione a `public` pasta às suas inclusões.
1. Na `ADBMobile-4.0.0BETA-BlackBerry` pasta, há um arquivo de `.json` configuração chamado `ADBMobileConfig.json`.

   Copie esse arquivo na raiz do seu projeto.
1. Clique com o botão direito do mouse em seu projeto e selecione **[!UICONTROL Atualizar]**.

   O `.json` arquivo agora deve estar visível no **[!UICONTROL Project Explorer]**.
1. Abra o `bar-descriptor.xml` arquivo do seu projeto.
1. Na parte inferior da janela, selecione a guia **[!UICONTROL Ativos]** .
1. Confirme se **[!UICONTROL (Todas as configurações)]** está selecionado e clique em **[!UICONTROL Adicionar arquivos]** na seção **[!UICONTROL Ativos]** da janela.
   >[!TIP]
   >
   >Há um bug no QNX Momentics IDE que às vezes impede que esses botões sejam visíveis. Se não conseguir ver os botões, redimensione as janelas até que eles apareçam.

1. Clique em **[!UICONTROL Espaço de trabalho]**.
1. Localize o `ADBMobileConfig.json` arquivo em seu projeto e clique em **[!UICONTROL OK]**.

Seu aplicativo pode importar classes/interfaces da `adobeMobileLibrary.jar` biblioteca usando `#include <ADBMobile.hpp>`.

## Adicionar permissões do aplicativo

No diretório `bar-descriptor.xml` do projeto, adicione a linha `<permission>access_internet</permission>`ou no QNX Momentics IDE, selecione a caixa **[!UICONTROL Internet]** na seção de permissões da guia **[!UICONTROL Aplicativo]** .

## Atualizar o arquivo de `ADBMobileConfig.json` configuração

O `ADBMobileConfig.json` arquivo contém configurações globais do SDK. É necessário atualizar alguns valores para começar.

The following is an example of an `ADBMobileConfig.json` file:

```json
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
    }
}
```

Você deve pelo menos atualizar os parâmetros `rsids` e `server` . Para obter mais detalhes, consulte Referência [de classe e método do](/help/blackberry/methods.md)Adobe Mobile.

Agora você pode implementar o Analytics no aplicativo BlackBerry 10.
