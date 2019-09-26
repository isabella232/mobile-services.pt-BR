---
description: 'null'
seo-description: 'null'
seo-title: Início rápido do desenvolvedor
solution: Marketing Cloud,Analytics
title: Developer quick start
topic: Desenvolvedor e implementação
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start{#developer-quick-start}

Estas são algumas informações sobre como implementar a biblioteca da plataforma Universal Windows.

>[!IMPORTANT]
>
>Para implementar o SDK, você precisa do Visual Studio 2013 ou posterior.

## Obter o SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

After you unzip the [SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) file, you will have a separate folder for each supported architecture and platform combination. Você também terá um `ADBMobileConfig.json` arquivo. Para obter mais informações sobre esse arquivo, consulte o arquivo [de configuração](/help/universal-windows/c-configuration/c.json.md)ADBMobileConfig.json.

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll/.winmd` files are provided for each supported architecture (x86, x64, ARM).

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. O `.winmd` arquivo contém apenas metadados e tem um número de versão de `255.255.255.255`, que é um comportamento aceito de acordo com a Microsoft. Para obter mais informações, consulte [Como adicionar informações de montagem para uma dll do componente WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Diferenças de sintaxe {#section_A02DE120B6D240F5AFFE7509755C4F14}

A biblioteca da plataforma Universal Windows pode ser usada em diversas linguagens de programação. Os exemplos neste guia estão em WinJS (JavaScript), se você estiver usando uma linguagem diferente, talvez precise ser modificada. Ao consumir métodos winmd de winJS, todos os métodos têm automaticamente a primeira letra em minúsculas.

A diferença principal entre as implementações é a estrutura de dados usada para dados de contexto. Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie o Visual Studio e abra sua solução.
1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Selecione a versão correta da biblioteca e navegue até o arquivo ADBMobile.winmd associado.

   Para obter mais informações, consulte *Selecionar a seção da versão* correta nesta página.

1. Clique em **Adicionar**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Se você também tiver um projeto C++ em sua solução, pule esta etapa.

1. Na guia **[!UICONTROL Windows]** à esquerda, selecione **[!UICONTROL Extensões]**, selecione e adicione **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**.

1. Adicione a seguinte linha à sua classe:

   ```csharp
   using ADBMobile;
   ```

1. Right-click your project and click **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Clique com o botão direito do mouse no `ADBMobileConfig.json` arquivo da solução e selecione **[!UICONTROL Propriedades]**.

1. Altere **[!UICONTROL Ação de montagem]** para **[!UICONTROL Conteúdo]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie o Visual Studio e abra sua solução.
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Selecione a versão correta da biblioteca e adicione uma referência ao arquivo ADBMobile.winmd associado.

   Para obter mais informações, consulte *Selecionar a seção da versão* correta nesta página.

1. Clique em **[!UICONTROL Adicionar]**.

1. Verifique se `ADBMobile.winmd` está selecionada na janela **Reference Manager (Gerenciador de referência** e clique em **[!UICONTROL OK]**.

1. Adicione a seguinte linha à sua classe:

   ```c++
   using namespace ADBMobile;
   ```

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]** and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie o Visual Studio e abra sua solução.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Selecione a versão correta da biblioteca e navegue até o arquivo ADBMobile.winmd associado.

1. Clique em **[!UICONTROL Adicionar]**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Se você também tiver um projeto C++ em sua solução, pule esta etapa.

1. Na guia **[!UICONTROL Windows]** à esquerda, selecione **[!UICONTROL Extensões]** e selecione e adicione **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**.

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Com Propriedades **** de arquivo selecionado, verifique se Ação **** do pacote está definida como **[!UICONTROL Conteúdo]**.

   Para projetos JavaScript, o arquivo é definido como Conteúdo por padrão.

## Update The ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

The `ADBMobileConfig.json` file contains global SDK settings and is located at your project root after you complete the steps in the *Add the library and config file to your project* section. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

Este é um exemplo de um arquivo `ADBMobileConfig.json`:

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

No mínimo, atualize os seguintes valores para as soluções que você está usando:

* **Adobe Analytics**: `rsids` e `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Para obter mais informações, consulte Métodos [do](/help/universal-windows/c-configuration/methods.md)SDK.

## Depuração {#section_3A10376A60394A15BEE483323E0CD4AA}

Para ativar a depuração para o SDK, chame `ADBMobile.Config.setDebugLogging(true);`.

Para aplicativos C Sharp e JavaScript, é necessário ativar a depuração de código nativa ao concluir as seguintes etapas (a depuração de código nativa é a configuração padrão para aplicativos C++):

### C Sharp

1. Clique com o botão direito do mouse no projeto e clique em **[!UICONTROL Propriedades]** &gt; guia **[!UICONTROL Depurar]**.

1. Altere o menu suspenso do tipo de depurador para **Apenas nativo**.

### JavaScript

1. Right-click the project, click **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**.

1. Altere o menu suspenso do tipo de depurador para **[!UICONTROL Apenas nativo]**.

Pronto! Você está pronto para implementar o Analytics, Target, e Gerenciamento de público-alvo no aplicativo da plataforma Universal Windows Platform app.

