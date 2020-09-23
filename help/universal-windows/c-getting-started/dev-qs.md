---
description: 'null'
seo-description: 'null'
seo-title: Início rápido do desenvolvedor
solution: Experience Cloud,Analytics
title: Início rápido do desenvolvedor
topic: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 4%

---


# Início rápido do desenvolvedor{#developer-quick-start}

Estas são algumas informações sobre como implementar a biblioteca da plataforma Universal Windows.

>[!IMPORTANT]
>
>Para implementar o SDK, você precisa do Visual Studio 2013 ou posterior.

## Obter o SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

Depois de descompactar o arquivo de download [do](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) SDK, você terá uma pasta separada para cada combinação de arquitetura e plataforma suportada. Você também terá um `ADBMobileConfig.json` arquivo. Para obter mais informações sobre esse arquivo, consulte o arquivo [de configuração](/help/universal-windows/c-configuration/c.json.md)ADBMobileConfig.json.

## Selecione a versão correta {#section_E53C5AA7D5474824A89BB32C003865A1}

Diferentes `.dll/.winmd` arquivos são fornecidos para cada arquitetura suportada (x86, x64, ARM).

>[!IMPORTANT]
>
>A versão do não `ADBMobile.winmd` reflete a versão da biblioteca. O `.winmd` arquivo contém apenas metadados e tem um número de versão de `255.255.255.255`, que é um comportamento aceito de acordo com a Microsoft. Para obter mais informações, consulte [Como adicionar informações de montagem para uma dll do componente WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Para verificar a versão da biblioteca que você está usando, verifique a versão do arquivo subjacente `ADBMobile.dll` .

## Diferenças de sintaxe {#section_A02DE120B6D240F5AFFE7509755C4F14}

A biblioteca da plataforma Universal Windows pode ser usada em várias linguagens de programação. Os exemplos neste guia estão em WinJS (JavaScript), se você estiver usando uma linguagem diferente, talvez precise ser modificada. Quando você consome métodos winmd de winJS, todos os métodos têm automaticamente a primeira letra em minúsculas.

A principal diferença entre as implementações é a estrutura de dados usada para dados de contexto. Além disso, ao usar o SDK em um projeto WinJS, use uma string vazia ( `""` ou `''`) em vez de `null` valores de string vazios.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie o Visual Studio e abra sua solução.
1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse em **[!UICONTROL Referências]** e selecione **[!UICONTROL Adicionar referência]**.

1. Selecione a versão correta da biblioteca e navegue até o arquivo ADBMobile.winmd associado.

   Para obter mais informações, consulte *Selecionar a seção da versão* correta nesta página.

1. Clique em **Adicionar**.

1. Verifique se o arquivo ADBMobile.winmd está marcado na janela Gerenciador **[!UICONTROL de]** referência e clique em **[!UICONTROL OK]**.

1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse em **[!UICONTROL Referências]** e selecione **[!UICONTROL Adicionar referência]**.

   Se você também tiver um projeto C++ em sua solução, pule esta etapa.

1. Na guia **[!UICONTROL Windows]** à esquerda, selecione **[!UICONTROL Extensões]**, selecione e adicione **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**.

1. Adicione a seguinte linha à sua classe:

   ```csharp
   using ADBMobile;
   ```

1. Clique com o botão direito do mouse em seu projeto e clique em **[!UICONTROL Adicionar]** > Item **[!UICONTROL existente]**.

1. Navegue até o `ADBMobileConfig.json` arquivo e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no `ADBMobileConfig.json` arquivo da solução e selecione **[!UICONTROL Propriedades]**.

1. Altere **[!UICONTROL Criar ação]** para **[!UICONTROL Conteúdo]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie o Visual Studio e abra sua solução.
1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse em seu projeto e selecione **[!UICONTROL Adicionar]** > **[!UICONTROL Referências]**.

1. Selecione a versão correta da biblioteca e adicione uma referência ao arquivo ADBMobile.winmd associado.

   Para obter mais informações, consulte *Selecionar a seção da versão* correta nesta página.

1. Clique em **[!UICONTROL Adicionar]**.

1. Verifique se `ADBMobile.winmd` está marcada na janela Gerenciador **[!UICONTROL de]** referência e clique em **[!UICONTROL OK]**.

1. Adicione a seguinte linha à sua classe:

   ```c++
   using namespace ADBMobile;
   ```

1. Clique com o botão direito do mouse em seu projeto e selecione **[!UICONTROL Adicionar]** > Item **[!UICONTROL existente]**.

1. Navegue até o `ADBMobileConfig.json` arquivo e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no `ADBMobileConfig.json` arquivo na solução e selecione **[!UICONTROL Propriedades]**.

1. Na guia **[!UICONTROL Geral]** , altere **[!UICONTROL Conteúdo]** para **[!UICONTROL Sim]** e clique em **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie o Visual Studio e abra sua solução.

1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse em **[!UICONTROL Referências]** e selecione **[!UICONTROL Adicionar referência]**.

1. Selecione a versão correta da biblioteca e navegue até o arquivo ADBMobile.winmd associado.

1. Clique em **[!UICONTROL Adicionar]**.

1. Verifique se o arquivo ADBMobile.winmd está marcado na janela Gerenciador **[!UICONTROL de]** referência e clique em **[!UICONTROL OK]**.

1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse em **[!UICONTROL Referências]** e selecione **[!UICONTROL Adicionar referência]**.

   Se você também tiver um projeto C++ em sua solução, pule esta etapa.

1. Na guia **[!UICONTROL Windows]** à esquerda, selecione **[!UICONTROL Extensões]** e selecione e adicione **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**.

1. Clique com o botão direito do mouse em seu projeto e selecione **[!UICONTROL Adicionar]** > Item **[!UICONTROL existente]**.

1. Navegue até o `ADBMobileConfig.json` arquivo e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no `ADBMobileConfig.json` arquivo na solução e selecione **[!UICONTROL Propriedades]**.

1. Com Propriedades **** de arquivo selecionado, verifique se Ação **** do pacote está definida como **[!UICONTROL Conteúdo]**.

   Para projetos JavaScript, o arquivo é definido como Conteúdo por padrão.

## Atualizar o arquivo de configuração ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

O `ADBMobileConfig.json` arquivo contém configurações globais do SDK e está localizado na raiz do projeto depois que você concluir as etapas em *Adicionar a biblioteca e o arquivo de configuração à seção do projeto* . Se seu `ADBMobileConfig.json` arquivo não foi pré-configurado pelo Adobe Mobile Services, é necessário atualizar alguns valores para começar.

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

For more information, see [SDK methods](/help/universal-windows/c-configuration/methods.md).

## Depuração {#section_3A10376A60394A15BEE483323E0CD4AA}

Para ativar a depuração para o SDK, chame `ADBMobile.Config.setDebugLogging(true);`.

Para aplicativos C Sharp e JavaScript, é necessário ativar a depuração de código nativa ao concluir as seguintes etapas (a depuração de código nativa é a configuração padrão para aplicativos C++):

### C Sharp

1. Clique com o botão direito do mouse no projeto e clique em **[!UICONTROL Propriedades]** > guia **[!UICONTROL Depurar]**.

1. Altere o menu suspenso do tipo de depurador para Somente **nativo**.

### JavaScript

1. Clique com o botão direito do mouse no projeto e clique em **[!UICONTROL Propriedades]** > Propriedades **** de configuração > guia **[!UICONTROL Depurar]**.

1. Altere o menu suspenso do tipo de depurador para Somente **[!UICONTROL nativo]**.

Pronto! Agora você está pronto para implementar o Analytics, o Público alvo e o Gerenciamento de Audiências no aplicativo da plataforma Universal Windows.

