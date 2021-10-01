---
title: Início rápido para desenvolvedores
description: O Guia de início rápido do desenvolvedor do BlackBerry ajuda você a entender o processo de implementação da biblioteca do BlackBerry para Adobe Mobile Services.
exl-id: 65f39667-541a-4bbd-af9b-823638aa6f42
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 1%

---

# Início rápido do desenvolvedor

Essas informações ajudam você a entender o processo de implementação da biblioteca do BlackBerry.

## Obter o SDK

**O SDK requer o BlackBerry 10 ou uma versão posterior.**

Após descompactar o SDK baixado, verifique se os seguintes arquivos existem em uma pasta `AdobeMobile`:

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

## Adicionar os SDKs ao projeto

1. Clique com o botão direito do mouse em seu projeto e selecione **[!UICONTROL Configurar]** > **[!UICONTROL Adicionar biblioteca]**.
1. Selecione **[!UICONTROL Biblioteca externa]** e clique em **[!UICONTROL Próximo]**.
1. Clique em **[!UICONTROL Procurar]** ao lado do campo **[!UICONTROL Biblioteca de dispositivos]**.
1. Navegue até a pasta `ADBMobile-4.0.0BETA-BlackBerry`.
1. Na pasta `Device-Debug`, selecione `libADBMobileShared.so` e clique em **[!UICONTROL Abrir]**.
1. Clique em **[!UICONTROL Procurar]** ao lado do campo **[!UICONTROL Biblioteca do simulador]**.
1. Navegue até a pasta `ADBMobile-4.0.0BETA-BlackBerry`.
1. Na pasta `Device-Debug`, selecione `libADBMobileShared.so` e clique em **[!UICONTROL Abrir]**.
1. Clique em **[!UICONTROL Adicionar]** ao lado do campo **[!UICONTROL Incluir pastas]**.
1. Navegue até a pasta `ADBMobile-4.0.0BETA-BlackBerry`.
1. Adicione a pasta `public` às suas inclusões.
1. Na pasta `ADBMobile-4.0.0BETA-BlackBerry`, há um arquivo de configuração `.json` chamado `ADBMobileConfig.json`.

   Copie esse arquivo na raiz do projeto.
1. Clique com o botão direito do mouse em seu projeto e selecione **[!UICONTROL Refresh]**.

   O arquivo `.json` agora deve estar visível no **[!UICONTROL Explorador de projetos]**.
1. Abra o arquivo `bar-descriptor.xml` para seu projeto.
1. Na parte inferior da janela, selecione a guia **[!UICONTROL Assets]**.
1. Confirme se **[!UICONTROL (Todas as configurações)]** está selecionado e clique em **[!UICONTROL Adicionar arquivos]** na seção **[!UICONTROL Ativos]** da janela.
   >[!TIP]
   >
   >Há um bug no QNX Momentics IDE que às vezes impede que esses botões sejam visíveis. Se não conseguir ver os botões, redimensione as janelas até que eles sejam exibidos.

1. Clique em **[!UICONTROL Workspace]**.
1. Localize o arquivo `ADBMobileConfig.json` em seu projeto e clique em **[!UICONTROL OK]**.

Seu aplicativo pode importar classes/interfaces da biblioteca `adobeMobileLibrary.jar` usando `#include <ADBMobile.hpp>`.

## Adicionar permissões do aplicativo

Em `bar-descriptor.xml` no diretório do projeto, adicione a linha `<permission>access_internet</permission>` ou no QNX Momentics IDE, selecione a caixa **[!UICONTROL Internet]** na seção de permissões da guia **[!UICONTROL Application]**.

## Atualize o arquivo de configuração `ADBMobileConfig.json`

O arquivo `ADBMobileConfig.json` contém configurações globais do SDK. Você precisa atualizar alguns valores para começar.

Este é um exemplo de um arquivo `ADBMobileConfig.json`:

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

Você deve pelo menos atualizar os parâmetros `rsids` e `server`. Para obter mais detalhes, consulte [Adobe Mobile class and method reference](/help/blackberry/methods.md).

Agora é possível implementar o Analytics no aplicativo BlackBerry 10.
