---
description: 'null'
seo-description: 'null'
seo-title: Início rápido do desenvolvedor
solution: Experience Cloud,Analytics
title: Início rápido do desenvolvedor
topic: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 3%

---


# Início rápido do desenvolvedor {#developer-quick-start}

Você precisará do Visual Studio 2013 ou posterior para implementar o SDK.

## Obter o SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

Depois de descompactar o download [do](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)SDK, você terá uma pasta separada para cada combinação de arquitetura e plataforma suportada. Você também terá um `ADBMobileConfig.json` arquivo que será explicado posteriormente neste guia.

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Diferentes arquivos `.dll`/ `.winmd` são fornecidos para cada plataforma de público alvo (Windows 8.1, Windows Phone 8.1) e arquitetura compatível (x86, x64, ARM). Os arquivos são separados em uma estrutura de pastas de acordo com o seguinte:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>A versão do não `ADBMobile.winmd` reflete a versão da biblioteca. O `.winmd` arquivo contém apenas metadados e, como tal, terá um número de versão do `255.255.255.255` qual é um comportamento aceito de acordo com a Microsoft (consulte [Como adicionar informações de montagem para uma dll do componente WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Para verificar a versão da biblioteca que você está usando, verifique a versão do arquivo subjacente `ADBMobile.dll` .

## Diferenças de sintaxe {#section_A02DE120B6D240F5AFFE7509755C4F14}

A biblioteca da loja de aplicativos universal do Windows 8.1 pode ser usada em várias linguagens de programação. Os exemplos neste guia estão em WinJS (JavaScript) e podem precisar ser modificados se você estiver usando uma linguagem diferente. Observe que ao consumir métodos winmd de winJS (JavaScript), todos os métodos têm automaticamente a primeira letra em minúsculas.

A principal diferença entre as implementações é a estrutura de dados usada para dados de contexto.

Além disso, ao usar o SDK em um projeto WinJS, use uma string vazia ( `""` ou `''`) em vez de `null` valores de string vazios.

## Adicionar a biblioteca e o arquivo de configuração ao seu projeto - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie o Visual Studio e abra sua solução.
1. No **Solution Explorer**, clique com o botão direito do mouse em **[!UICONTROL Referências]** e selecione **[!UICONTROL Adicionar referência]**.

1. Selecione a versão correta da biblioteca e navegue até o arquivo associado. `ADBMobile.winmd`

   Para obter mais informações, consulte a seção *Selecionar a versão* correta abaixo.

1. Clique em **[!UICONTROL Adicionar]**.

1. Verifique se `ADBMobile.winmd` está selecionado na janela Gerenciador **[!UICONTROL de]** referência e clique em **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Ao adicionar uma referência a um aplicativo do Windows Phone, para selecionar `ADBMobile.winmd`, altere o filtro de arquivo padrão de Arquivos **[!UICONTROL de]** componentes para **Todos os arquivos**.

1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse em **[!UICONTROL Referências]** e selecione **[!UICONTROL Adicionar referência]**.

   Ignore esta etapa se você também tiver um projeto C++ em sua solução.

1. Na guia **Windows** à esquerda, selecione **[!UICONTROL Extensões]** e, em seguida, selecione e adicione **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Adicione a seguinte linha à sua classe:

   ```
   using ADBMobile;
   ```

1. Clique com o botão direito do mouse em seu projeto e selecione **[!UICONTROL Adicionar]** > Item **[!UICONTROL existente]**.

1. Navegue até o seu `ADBMobileConfig.json` arquivo e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no `ADBMobileConfig.json` arquivo na solução e selecione **[!UICONTROL Propriedades]**.

1. Altere **[!UICONTROL Criar ação]** para **[!UICONTROL Conteúdo]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie o Visual Studio e abra sua solução.
1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse em seu projeto e selecione **[!UICONTROL Adicionar]** > **[!UICONTROL Referências]**.

1. Selecione a versão correta da biblioteca e adicione uma referência ao arquivo associado. `ADBMobile.winmd`

   Para obter mais informações, consulte a seção *Selecionar a versão* correta abaixo.

1. Clique em **[!UICONTROL Adicionar]**.

1. Na janela Gerenciador **[!UICONTROL de]** referência, verifique se `ADBMobile.winmd` está selecionado e clique em **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Ao adicionar uma referência a um aplicativo do Windows Phone, para selecionar `ADBMobile.winmd`, altere o filtro de arquivo padrão de Arquivos **[!UICONTROL de]** componentes para **Todos os arquivos**.

1. Adicione a seguinte linha à sua classe:

   ```
   using namespace ADMS::Measurement;
   ```

1. Clique com o botão direito do mouse em seu projeto e selecione **[!UICONTROL Adicionar]** > Item **[!UICONTROL existente]**.

1. Navegue até o `ADBMobileConfig.json` arquivo e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no `ADBMobileConfig.json` arquivo na solução e selecione **[!UICONTROL Propriedades]**.

1. Na guia **[!UICONTROL Geral]** , altere **[!UICONTROL Conteúdo]** para **[!UICONTROL Sim]** e clique em **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie o Visual Studio e abra sua solução.
1. No **Solution Explorer**, clique com o botão direito do mouse em **[!UICONTROL Referências]** e selecione **[!UICONTROL Adicionar referência]**.

   Para obter mais informações, consulte a seção *Selecionar a versão* correta abaixo.

1. Selecione a versão correta da biblioteca e navegue até o arquivo associado. `ADBMobile.winmd`

1. Clique em **[!UICONTROL Adicionar]**.

1. Verifique se `ADBMobile.winmd` está marcada na janela Gerenciador **[!UICONTROL de]** referência e clique em **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Ao adicionar uma referência a um aplicativo do Windows Phone, para selecionar `ADBMobile.winmd`, altere o filtro de arquivo padrão de Arquivos **[!UICONTROL de]** componentes para **Todos os arquivos**.

1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse em **[!UICONTROL Referências]** e selecione **[!UICONTROL Adicionar referência]**.

   Ignore esta etapa se você também tiver um projeto C++ em sua solução.

1. Na guia **[!UICONTROL Windows]** à esquerda, selecione **[!UICONTROL Extensões]** e selecione e adicione o Pacote de tempo de execução **[!UICONTROL Microsoft Visual C++ 2013 para Windows]**.

1. Clique com o botão direito do mouse em seu projeto e selecione **[!UICONTROL Adicionar]** > Item **[!UICONTROL existente]**.

1. Navegue até o `ADBMobileConfig.json` arquivo e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no `ADBMobileConfig.json]` arquivo na solução e selecione **[!UICONTROL Propriedades]**.

1. Com Propriedades **** de arquivo selecionado, verifique se Ação **** do pacote está definida como **[!UICONTROL Conteúdo]**.

   Para projetos JavaScript, o arquivo é definido como **[!UICONTROL Conteúdo]** por padrão.

## Atualize o arquivo de configuração ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

O `ADBMobileConfig.json` arquivo contém configurações globais do SDK e está localizado na raiz do projeto depois que você concluir as etapas em *Adicionar a biblioteca e o arquivo de configuração à seção Projeto* . Se seu `ADBMobileConfig.json` arquivo não foi pré-configurado pelo Adobe Mobile Services, é necessário atualizar alguns valores para começar.

The following is an example of an `ADBMobileConfig.json` file:

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

No mínimo, atualize os seguintes valores para as Soluções que você está usando:

* **Analytics**: `rsids` e `server`
* **Target**: `clientCode`
* **Gerenciamento de público-alvo**: `server`

Para obter mais detalhes, consulte [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## Depuração {#section_3A10376A60394A15BEE483323E0CD4AA}

Quando você quiser ativar a depuração para o SDK, é necessário chamar `ADBMobile.Config.setDebugLogging(true);`.

Para aplicativos C Sharp e JS, é necessário ativar a depuração de código nativa completando as seguintes etapas (a depuração de código nativa é a configuração padrão para aplicativos C++):

### C Sharp

Clique com o botão direito do mouse no projeto e selecione **[!UICONTROL Propriedades]** > guia **[!UICONTROL Depurar]**. Na lista suspensa do depurador, selecione Somente **[!UICONTROL nativo]**.

### JS

Clique com o botão direito do mouse no projeto e selecione **[!UICONTROL Propriedades]** > Propriedades **** de configuração > guia **[!UICONTROL Depurar]**. Altere o menu suspenso do tipo de depurador para Somente **nativo**.

Pronto! Agora você está pronto para implementar o Analytics, o Público alvo e o Gerenciamento de Audiências no aplicativo da loja de aplicativos universal do Windows 8.1.
