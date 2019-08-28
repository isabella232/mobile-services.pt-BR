---
title: Início rápido para desenvolvedores
seo-title: Introdução rápida do blackberry Developer para Adobe Mobile Services
description: O Guia de início rápido do blackberry Developer ajuda você a entender o processo de implementação da biblioteca do blackberry para Adobe Mobile Services.
seo-description: O Guia de início rápido do blackberry Developer ajuda você a entender o processo de implementação da biblioteca do blackberry para Adobe Mobile Services.
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Início rápido do desenvolvedor

Estas informações ajudam você a entender o processo de implementação da biblioteca do BlackBerry.

## Obter o SDK

**O SDK requer o BlackBerry 10 ou uma versão mais recente.**

Depois de descompactar o SDK baixado, verifique se os arquivos a seguir estão em uma pasta `AdobeMobile`:

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

## Adicionar os SDKs a seu projeto

1. Right-click on your project and select **[!UICONTROL Configure]** &gt; **[!UICONTROL Add Library]**.
1. Selecione **[!UICONTROL Biblioteca externa]** e clique em **[!UICONTROL Avançar]**.
1. Clique em **[!UICONTROL Pesquisar]** próximo ao campo **Biblioteca do dispositivo[!UICONTROL .]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. Clique em **[!UICONTROL Pesquisar]** próximo ao campo **Biblioteca do simulador[!UICONTROL .]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. Clique em **[!UICONTROL Adicionar]** próximo ao campo **Incluir pastas[!UICONTROL .]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Adicione a pasta `public` às suas inclusões.
1. In the `ADBMobile-4.0.0BETA-BlackBerry` folder, there is a `.json` config file named `ADBMobileConfig.json`.

   Copie esse arquivo para a raiz de seu projeto.
1. Right-click on your project and select **[!UICONTROL Refresh]**.

   The `.json` file should now be visible in your **[!UICONTROL Project Explorer]**.
1. Abra o arquivo `bar-descriptor.xml` referente a seu projeto.
1. Na parte inferior da janela, selecione a guia **[!UICONTROL Ativos].**
1. Confirme se a opção **[!UICONTROL (Todas as configurações)]** está selecionada e clique em **[!UICONTROL Adicionar arquivos]na seção** Ativos] da janela.**[!UICONTROL **
   >[!TIP]
   >
   >Há um erro no QNX Momentics IDE que às vezes impede que esses botões sejam visualizados. Caso não consiga visualizá-los, redimensione as janelas até que eles apareçam.

1. Clique em **[!UICONTROL Espaço de trabalho]**.
1. Localize o arquivo `ADBMobileConfig.json`**em seu projeto e clique em[!UICONTROL OK]**.

Seu aplicativo pode importar classificações/interfaces da biblioteca `adobeMobileLibrary.jar` usando `#include <ADBMobile.hpp>`.

## Adicionar permissões de aplicativo

In `bar-descriptor.xml` in the project directory, add the line `<permission>access_internet</permission>`, or in the QNX Momentics IDE, select the **[!UICONTROL Internet]** box on the permissions section of the **[!UICONTROL Application]** tab.

## Update the `ADBMobileConfig.json` config file

O arquivo `ADBMobileConfig.json` contém configurações globais do SDK. É necessário atualizar alguns valores para começar.

A seguir, um exemplo de um arquivo `ADBMobileConfig.json`:

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

You must at least update the `rsids` and `server` parameters. Para obter mais detalhes, consulte [Referência de método e classe do Adobe Mobile](/help/blackberry/methods.md).

Agora, é possível implementar o Analytics em seu aplicativo do BlackBerry 10.
