---
description: 'null'
seo-description: 'null'
seo-title: Início rápido do desenvolvedor
solution: Experience Cloud,Analytics
title: Início rápido do desenvolvedor
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 3%

---

# Início rápido do desenvolvedor {#developer-quick-start}

Você precisará do Visual Studio 2013 ou posterior para implementar o SDK.

## Obter o SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

Depois de descompactar o [download do SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), você terá uma pasta separada para cada combinação de arquitetura e plataforma compatível. Você também terá um arquivo `ADBMobileConfig.json` que será explicado mais tarde neste guia.

## Selecione a versão correta {#section_E53C5AA7D5474824A89BB32C003865A1}

Arquivos `.dll`/ `.winmd` diferentes são fornecidos para cada plataforma de destino (Windows 8.1, Windows Phone 8.1) e arquitetura suportada (x86, x64, ARM). Os arquivos são separados em uma estrutura de pastas de acordo com o seguinte:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>A versão de `ADBMobile.winmd` não reflete a versão da biblioteca. O arquivo `.winmd` contém apenas metadados e, como tal, terá um número de versão `255.255.255.255` que é um comportamento aceito de acordo com a Microsoft (consulte [Como adicionar informações de montagem para uma dll de componente WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Para verificar a versão da biblioteca que você está usando, verifique a versão do arquivo `ADBMobile.dll` subjacente.

## Diferenças de sintaxe {#section_A02DE120B6D240F5AFFE7509755C4F14}

A biblioteca da loja de aplicativos universal do Windows 8.1 pode ser usada em várias linguagens de programação. Os exemplos neste guia estão em WinJS (JavaScript) e podem precisar ser modificados se você estiver usando uma linguagem diferente. Observe que ao consumir métodos winmd do winJS (JavaScript), todos os métodos passam a ter a primeira letra em minúsculas automaticamente.

A principal diferença entre as implementações é a estrutura de dados usada para dados de contexto.

Além disso, ao usar o SDK em um projeto WinJS, use uma string vazia ( `""` ou `''`) em vez de `null` para valores de string vazios.

## Adicionar a biblioteca e o arquivo de configuração ao seu projeto - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie o Visual Studio e abra sua solução.
1. No **Solution Explorer**, clique com o botão direito do mouse em **[!UICONTROL References]** e selecione **[!UICONTROL Add Reference]**.

1. Selecione a versão correta da biblioteca e navegue até o arquivo `ADBMobile.winmd` associado.

   Para obter mais informações, consulte a seção *Selecionar a versão correta* abaixo.

1. Clique em **[!UICONTROL Adicionar]**.

1. Verifique se `ADBMobile.winmd` está selecionado na janela **[!UICONTROL Gerenciador de Referência]** e clique em **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Ao adicionar uma referência a um aplicativo do Windows Phone, para selecionar `ADBMobile.winmd`, altere o filtro de arquivo padrão de **[!UICONTROL Arquivos de componente]** para **Todos os arquivos**.

1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse em **[!UICONTROL References]** e selecione **[!UICONTROL Add Reference]**.

   Pule esta etapa se você também tiver um projeto C++ em sua solução.

1. Na guia **Windows** à esquerda, selecione **[!UICONTROL Extensões]**, selecione e adicione **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Adicione a seguinte linha à sua classe:

   ```
   using ADBMobile;
   ```

1. Clique com o botão direito do mouse no seu projeto e selecione **[!UICONTROL Adicionar]** > **[!UICONTROL Item Existente]**.

1. Navegue até o arquivo `ADBMobileConfig.json` e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no arquivo `ADBMobileConfig.json` na solução e selecione **[!UICONTROL Propriedades]**.

1. Altere **[!UICONTROL Ação de compilação]** para **[!UICONTROL Conteúdo]**.

## Adicionar a biblioteca e o arquivo de configuração ao seu projeto - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie o Visual Studio e abra sua solução.
1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse no seu projeto e selecione **[!UICONTROL Add]** > **[!UICONTROL References]**.

1. Selecione a versão correta da biblioteca e adicione uma referência ao arquivo `ADBMobile.winmd` associado.

   Para obter mais informações, consulte a seção *Selecionar a versão correta* abaixo.

1. Clique em **[!UICONTROL Adicionar]**.

1. Na janela **[!UICONTROL Gerenciador de Referência]**, verifique se `ADBMobile.winmd` está selecionado e clique em **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Ao adicionar uma referência a um aplicativo do Windows Phone, para selecionar `ADBMobile.winmd`, altere o filtro de arquivo padrão de **[!UICONTROL Arquivos de componente]** para **Todos os arquivos**.

1. Adicione a seguinte linha à sua classe:

   ```
   using namespace ADMS::Measurement;
   ```

1. Clique com o botão direito do mouse no seu projeto e selecione **[!UICONTROL Adicionar]** > **[!UICONTROL Item Existente]**.

1. Navegue até o arquivo `ADBMobileConfig.json` e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no arquivo `ADBMobileConfig.json` na solução e selecione **[!UICONTROL Propriedades]**.

1. Na guia **[!UICONTROL Geral]**, altere **[!UICONTROL Conteúdo]** para **[!UICONTROL Sim]** e clique em **[!UICONTROL OK]**.

## Adicionar a biblioteca e o arquivo de configuração ao seu projeto - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie o Visual Studio e abra sua solução.
1. No **Solution Explorer**, clique com o botão direito do mouse em **[!UICONTROL References]** e selecione **[!UICONTROL Add Reference]**.

   Para obter mais informações, consulte a seção *Selecionar a versão correta* abaixo.

1. Selecione a versão correta da biblioteca e navegue até o arquivo `ADBMobile.winmd` associado.

1. Clique em **[!UICONTROL Adicionar]**.

1. Verifique se `ADBMobile.winmd` está selecionado na janela **[!UICONTROL Gerenciador de Referência]** e clique em **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Ao adicionar uma referência a um aplicativo do Windows Phone, para selecionar `ADBMobile.winmd`, altere o filtro de arquivo padrão de **[!UICONTROL Arquivos de componente]** para **Todos os arquivos**.

1. No **[!UICONTROL Solution Explorer]**, clique com o botão direito do mouse em **[!UICONTROL References]** e selecione **[!UICONTROL Add Reference]**.

   Pule esta etapa se você também tiver um projeto C++ em sua solução.

1. Na guia **[!UICONTROL Windows]** à esquerda, selecione **[!UICONTROL Extensões]** e selecione e adicione **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Clique com o botão direito do mouse no projeto e selecione **[!UICONTROL Adicionar]** > **[!UICONTROL Item Existente]**.

1. Navegue até o arquivo `ADBMobileConfig.json` e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no arquivo `ADBMobileConfig.json]` na solução e selecione **[!UICONTROL Propriedades]**.

1. Com **[!UICONTROL Propriedades do arquivo]** selecionado, verifique se **[!UICONTROL Ação do pacote]** está definida como **[!UICONTROL Conteúdo]**.

   Para projetos JavaScript, o arquivo é definido como **[!UICONTROL Content]** por padrão.

## Atualize o arquivo de configuração ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

O arquivo `ADBMobileConfig.json` contém configurações globais do SDK e está localizado na raiz do projeto após concluir as etapas na seção *Adicionar a biblioteca e o arquivo de configuração ao projeto*. Se o arquivo `ADBMobileConfig.json` não tiver sido pré-configurado pelo Adobe Mobile Services, será necessário atualizar alguns valores para começar.

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

No mínimo, atualize os seguintes valores para as Soluções que estiver usando:

* **Analytics**:  `rsids` e  `server`
* **Target**: `clientCode`
* **Gerenciamento de público-alvo**: `server`

Para obter mais detalhes, consulte [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## Depuração {#section_3A10376A60394A15BEE483323E0CD4AA}

Quando quiser habilitar a depuração no SDK, é necessário chamar `ADBMobile.Config.setDebugLogging(true);`.

Para aplicativos em C Sharp e JS, é necessário habilitar a depuração de código nativa ao concluir as seguintes etapas (a depuração de código nativa é a configuração padrão para aplicativos em C++):

### C Nitidez

Clique com o botão direito do mouse no projeto e selecione **[!UICONTROL Properties]** > **[!UICONTROL Debug tab]**. Na lista suspensa do depurador, selecione **[!UICONTROL Somente nativo]**.

### JS

Clique com o botão direito do mouse no projeto e selecione **[!UICONTROL Propriedades]** > **[!UICONTROL Propriedades de configuração]** > **[!UICONTROL Depurar guia]**. Altere o menu suspenso do tipo de depurador para **Somente nativo**.

Pronto! Agora você está pronto para implementar o Analytics, Target e Gerenciamento de público-alvo no aplicativo da loja de aplicativos universal do Windows 8.1.
