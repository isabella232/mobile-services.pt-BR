---
description: 'null'
seo-description: 'null'
seo-title: Início rápido do desenvolvedor
solution: Marketing Cloud, Analytics
title: Início rápido do desenvolvedor
topic: Desenvolvedor e implementação
uuid: b 368959 b-d 985-436 e -8 b 3 e -97 e 355 a 97951
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start {#developer-quick-start}

Será necessário o Visual Studio 2013 ou posteriores para implementar o SDK.

## Obter o SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

Após descompactar o [download do SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), você terá uma pasta separada para cada combinação de arquitetura e plataforma compatível. Você também terá um arquivo `ADBMobileConfig.json` que será explicado mais tarde neste guia.

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll`/ `.winmd` files are provided for each target platform (Windows 8.1, Windows Phone 8.1), and supported architecture (x86, x64, ARM). Os arquivos são separados em uma estrutura de pastas de acordo com o seguinte:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. The `.winmd` file contains metadata only, and as such will have a version number of `255.255.255.255` which is accepted behavior according to Microsoft (see [How do I add assembly information for a WinRT C++ / CX component dll?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Syntax differences {#section_A02DE120B6D240F5AFFE7509755C4F14}

É possível usar a biblioteca da loja de aplicativos universal do Windows 8.1 em várias linguagens de programação. Os exemplos neste guia estão em WinJS (JavaScript) e pode ser necessário modificá-los se você estiver usando uma linguagem diferente. Observe que ao consumir métodos winmd do winJS (JavaScript), todos os métodos passam a ter a primeira letra em minúsculas automaticamente.

A diferença principal entre as implementações é a estrutura de dados usada para dados de contexto.

Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config file to your project - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie o Visual Studio e abra sua solução.
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UIUCONTROL Add Reference]**.

1. Select the correct version of the library and browse to the associated `ADBMobile.winmd` file.

   Para obter mais informações, consulte a *seção Selecionar a versão* correta abaixo.

1. Clique em **[!UICONTROL Adicionar]**.

1. Verify that `ADBMobile.winmd` is selected in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Ao adicionar uma referência a um aplicativo do Windows Phone, a fim de selecionar `ADBMobile.winmd`, altere o filtro de arquivos padrão dos Arquivos **[!UICONTROL de componente]** para **Todos os arquivos**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Pule esta etapa se você também tem um projeto em C + + na solução.

1. Na guia **Windows** à esquerda, selecione **[!UICONTROL Extensões]**, em seguida, selecione e adicione **[!UICONTROL Microsoft Visual Studio C + + 2013 Runtime Package for Windows]**.

1. Adicione a seguinte linha à sua classe:

   ```
   using ADBMobile;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Navegue até seu `ADBMobileConfig.json` arquivo e clique **[!UICONTROL em Adicionar]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Altere **[!UICONTROL Ação de montagem]** para **[!UICONTROL Conteúdo]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie o Visual Studio e abra sua solução.
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Select the correct version of the library and then add a reference to the associated `ADBMobile.winmd` file.

   Para obter mais informações, consulte *a seção Selecionar a versão* correta abaixo.

1. Clique em **[!UICONTROL Adicionar]**.

1. Na janela **[!UICONTROL Gerenciador]** de referência, verifique se `ADBMobile.winmd` está selecionada e clique **[!UICONTROL em OK]**.

   >[!TIP]
   >
   >Ao adicionar uma referência a um aplicativo do Windows Phone, a fim de selecionar `ADBMobile.winmd`, altere o filtro de arquivos padrão dos Arquivos **[!UICONTROL de componente]** para **Todos os arquivos**.

1. Adicione a seguinte linha à sua classe:

   ```
   using namespace ADMS::Measurement;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]**, and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie o Visual Studio e abra sua solução.
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference**.

   Para obter mais informações, consulte *Selecionar a seção Versão* correta abaixo.

1. Select the correct version of the library and then browse to the associated `ADBMobile.winmd` file.

1. Clique em **[!UICONTROL Adicionar]**.

1. Verifique se `ADBMobile.winmd` está selecionada na janela **Reference Manager (Gerenciador de referência** e clique em **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Ao adicionar uma referência a um aplicativo do Windows Phone, a fim de selecionar `ADBMobile.winmd`, altere o filtro de arquivos padrão dos Arquivos **[!UICONTROL de componente]** para **Todos os arquivos**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Pule esta etapa se você também tem um projeto em C + + na solução.

1. Na guia **[!UICONTROL Windows]** à esquerda, selecione **[!UICONTROL Extensões]** , selecione e adicione **[!UICONTROL Microsoft Visual Studio C + + 2013 Runtime Package for Windows]**.

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json]` file in your solution and select **[!UICONTROL Properties]**.

1. Com **[!UICONTROL Propriedades de arquivo]** selecionadas, verifique se **[!UICONTROL a Ação do pacote]** está definida como **[!UICONTROL Conteúdo]**.

   Para projetos javascript, o arquivo é definido como **[!UICONTROL Conteúdo]** por padrão.

## Update the ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

The `ADBMobileConfig.json` file contains global SDK settings, and is located at your project root after you complete the steps in the *Add the Library and Config File to your Project* section. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

A seguir, um exemplo de um arquivo `ADBMobileConfig.json`:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 1 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

No mínimo, atualize os seguintes valores para as soluções que estiver usando:

* **Analytics**: `rsids` e `server`
* **Target**: `clientCode`
* **Gerenciamento de público-alvo**: `server`

For more details, see [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## Depuração {#section_3A10376A60394A15BEE483323E0CD4AA}

Quando quiser habilitar a depuração no SDK, você deve chamar `ADBMobile.Config.setDebugLogging(true);`.

Para aplicativos C Sharp e JS, é necessário ativar a depuração de código nativa ao concluir as seguintes etapas (depuração de código nativa é a configuração padrão para aplicativos de C + +):

### C Sharp

Right-click the project, select **[!UICONTROL Properties]** &gt; **[!UICONTROL Debug tab]**. No menu suspenso do depurador, selecione **[!UICONTROL Somente nativo]**.

### JS

Right-click the project, select  **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**. Altere o menu suspenso do tipo de depurador para **Apenas nativo**.

Pronto! Agora você está pronto para implementar o Analytics, o Target e o Gerenciamento de público-alvo no seu aplicativo da loja de aplicativos universal do Windows 8.1.
