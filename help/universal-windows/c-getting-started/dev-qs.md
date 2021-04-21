---
description: Informações sobre como implementar a biblioteca da plataforma Universal Windows.
solution: Experience Cloud,Analytics
title: Início rápido do desenvolvedor
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 3%

---

# Início rápido do desenvolvedor{#developer-quick-start}

Estas são algumas informações sobre como implementar a biblioteca da plataforma Universal Windows.

>[!IMPORTANT]
>
>Para implementar o SDK, você precisa do Visual Studio 2013 ou posterior.

## Obter o SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

Depois de descompactar o arquivo de [download do SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), você terá uma pasta separada para cada combinação de arquitetura e plataforma compatível. Você também terá um arquivo `ADBMobileConfig.json`. Para obter mais informações sobre esse arquivo, consulte [Arquivo de configuração ADBMobileConfig.json](/help/universal-windows/c-configuration/c.json.md).

## Selecione a versão correta {#section_E53C5AA7D5474824A89BB32C003865A1}

Arquivos `.dll/.winmd` diferentes são fornecidos para cada arquitetura suportada (x86, x64, ARM).

>[!IMPORTANT]
>
>A versão de `ADBMobile.winmd` não reflete a versão da biblioteca. O arquivo `.winmd` contém apenas metadados e tem um número de versão `255.255.255.255`, que é um comportamento aceito de acordo com a Microsoft. Para obter mais informações, consulte [Como adicionar informações de montagem para uma dll do componente WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Para verificar a versão da biblioteca que você está usando, verifique a versão do arquivo `ADBMobile.dll` subjacente.

## Diferenças de sintaxe {#section_A02DE120B6D240F5AFFE7509755C4F14}

A biblioteca da plataforma Universal Windows pode ser usada em várias linguagens de programação. Os exemplos neste guia estão em WinJS (JavaScript), se você estiver usando uma linguagem diferente, talvez precise ser modificada. Ao consumir métodos winmd do winJS, todos os métodos passam a ter a primeira letra em minúsculas automaticamente.

A principal diferença entre as implementações é a estrutura de dados usada para dados de contexto. Além disso, ao usar o SDK em um projeto WinJS, use uma string vazia ( `""` ou `''`) em vez de `null` para valores de string vazios.

## Adicionar a biblioteca e o arquivo de configuração ao projeto - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie o Visual Studio e abra sua solução.
1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse em **[!UICONTROL References]** e selecione **[!UICONTROL Add Reference]**.

1. Selecione a versão correta da biblioteca e navegue até o arquivo ADBMobile.winmd associado.

   Para obter mais informações, consulte a seção *Selecionar a versão correta* nesta página.

1. Clique em **Adicionar**.

1. Verifique se o arquivo ADBMobile.winmd está marcado na janela **[!UICONTROL Gerenciador de Referência]** e clique em **[!UICONTROL OK]**.

1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse em **[!UICONTROL References]** e selecione **[!UICONTROL Add Reference]**.

   Se você também tiver um projeto C++ em sua solução, pule esta etapa.

1. Na guia **[!UICONTROL Windows]** à esquerda, selecione **[!UICONTROL Extensões]**, selecione e adicione **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**.

1. Adicione a seguinte linha à sua classe:

   ```csharp
   using ADBMobile;
   ```

1. Clique com o botão direito do mouse no projeto e clique em **[!UICONTROL Adicionar]** > **[!UICONTROL Item Existente]**.

1. Navegue até o arquivo `ADBMobileConfig.json` e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no arquivo `ADBMobileConfig.json` na solução e selecione **[!UICONTROL Propriedades]**.

1. Altere **[!UICONTROL Ação de compilação]** para **[!UICONTROL Conteúdo]**.

## Adicionar a biblioteca e o arquivo de configuração ao seu projeto - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie o Visual Studio e abra sua solução.
1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse no seu projeto e selecione **[!UICONTROL Add]** > **[!UICONTROL References]**.

1. Selecione a versão correta da biblioteca e adicione uma referência ao arquivo ADBMobile.winmd associado.

   Para obter mais informações, consulte a seção *Selecionar a versão correta* nesta página.

1. Clique em **[!UICONTROL Adicionar]**.

1. Verifique se `ADBMobile.winmd` está selecionado na janela **[!UICONTROL Gerenciador de Referência]** e clique em **[!UICONTROL OK]**.

1. Adicione a seguinte linha à sua classe:

   ```c++
   using namespace ADBMobile;
   ```

1. Clique com o botão direito do mouse no projeto e selecione **[!UICONTROL Adicionar]** > **[!UICONTROL Item Existente]**.

1. Navegue até `ADBMobileConfig.json` arquivo e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no arquivo `ADBMobileConfig.json` na solução e selecione **[!UICONTROL Propriedades]**.

1. Na guia **[!UICONTROL General]**, altere **[!UICONTROL Content]** para **[!UICONTROL Yes]** e clique em **[!UICONTROL OK]**.

## Adicionar a biblioteca e o arquivo de configuração ao seu projeto - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie o Visual Studio e abra sua solução.

1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse em **[!UICONTROL References]** e selecione **[!UICONTROL Add Reference]**.

1. Selecione a versão correta da biblioteca e navegue até o arquivo ADBMobile.winmd associado.

1. Clique em **[!UICONTROL Adicionar]**.

1. Verifique se o arquivo ADBMobile.winmd está marcado na janela **[!UICONTROL Gerenciador de Referência]** e clique em **[!UICONTROL OK]**.

1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse em **[!UICONTROL References]** e selecione **[!UICONTROL Add Reference]**.

   Se você também tiver um projeto C++ em sua solução, pule esta etapa.

1. Na guia **[!UICONTROL Windows]** à esquerda, selecione **[!UICONTROL Extensões]** e selecione e adicione **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**.

1. Clique com o botão direito do mouse no projeto e selecione **[!UICONTROL Adicionar]** > **[!UICONTROL Item Existente]**.

1. Navegue até o arquivo `ADBMobileConfig.json` e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no arquivo `ADBMobileConfig.json` na solução e selecione **[!UICONTROL Propriedades]**.

1. Com **[!UICONTROL Propriedades do arquivo]** selecionado, verifique se **[!UICONTROL Ação do pacote]** está definida como **[!UICONTROL Conteúdo]**.

   Para projetos JavaScript, o arquivo é definido como Conteúdo por padrão.

## Atualizar o arquivo de configuração ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

O arquivo `ADBMobileConfig.json` contém configurações globais do SDK e está localizado na raiz do projeto depois de concluir as etapas na seção *Adicionar a biblioteca e o arquivo de configuração ao projeto*. Se o arquivo `ADBMobileConfig.json` não tiver sido pré-configurado pelo Adobe Mobile Services, será necessário atualizar alguns valores para começar.

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

No mínimo, atualize os seguintes valores para as soluções que você estiver usando:

* **Adobe Analytics**:  `rsids` e  `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Para obter mais informações, consulte [Métodos do SDK](/help/universal-windows/c-configuration/methods.md).

## Depuração {#section_3A10376A60394A15BEE483323E0CD4AA}

Para habilitar a depuração no SDK, chame `ADBMobile.Config.setDebugLogging(true);`.

Para aplicativos em C Sharp e JavaScript, é necessário habilitar a depuração de código nativa ao concluir as seguintes etapas (a depuração de código nativa é a configuração padrão para aplicativos em C++):

### C Nitidez

1. Clique com o botão direito do mouse no projeto, clique em **[!UICONTROL Properties]** > **[!UICONTROL Debug tab]**.

1. Altere o menu suspenso do tipo de depurador para **Somente nativo**.

### JavaScript

1. Clique com o botão direito do mouse no projeto, clique em **[!UICONTROL Properties]** > **[!UICONTROL Configuration Properties]** > **[!UICONTROL Debug tab]**.

1. Altere o menu suspenso do tipo de depurador para **[!UICONTROL Somente nativo]**.

Pronto! Agora você está pronto para implementar o Analytics, Target e Gerenciamento de público-alvo no aplicativo da plataforma Universal Windows Platform.
