---
description: Artigo de início rápido do desenvolvedor
solution: Experience Cloud Services,Analytics
title: Início rápido do desenvolvedor
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 2%

---

# Início rápido do desenvolvedor {#developer-quick-start}

Você precisará do Visual Studio 2013 ou posterior para implementar o SDK.

## Obter o SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

Depois de descompactar o [Download do SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), você terá uma pasta separada para cada combinação de arquitetura e plataforma compatível. Você também terá um `ADBMobileConfig.json` arquivo que é explicado mais tarde neste guia.

## Selecione a versão correta {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll`/ `.winmd` os arquivos são fornecidos para cada plataforma de destino (Windows 8.1, Windows Phone 8.1) e arquitetura compatível (x86, x64, ARM). Os arquivos são separados em uma estrutura de pastas de acordo com o seguinte:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>A versão de `ADBMobile.winmd` não reflete a versão da biblioteca. O `.winmd` O arquivo contém somente metadados e, como tal, terá um número de versão de `255.255.255.255` que é um comportamento aceito de acordo com a Microsoft (consulte [Como adiciono informações de montagem para uma dll do componente WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Para verificar a versão da biblioteca que você está usando, verifique a versão do subjacente `ADBMobile.dll` arquivo.

## Diferenças de sintaxe {#section_A02DE120B6D240F5AFFE7509755C4F14}

A biblioteca Universal App Store do Windows 8.1 pode ser usada em várias linguagens de programação. Os exemplos neste guia estão em WinJS (JavaScript) e podem precisar ser modificados se você estiver usando uma linguagem diferente. Observe que ao consumir métodos winmd do winJS (JavaScript), todos os métodos passam a ter a primeira letra em minúsculas automaticamente.

A principal diferença entre as implementações é a estrutura de dados usada para dados de contexto.

Além disso, ao usar o SDK em um projeto WinJS, use uma string vazia ( `""` ou `''`) em vez de `null` para valores de string vazios.

## Adicionar a biblioteca e o arquivo de configuração ao seu projeto - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie o Visual Studio e abra sua solução.
1. No **Explorador de soluções**, clique com o botão direito do mouse **[!UICONTROL Referências]** e selecione **[!UICONTROL Adicionar referência]**.

1. Selecione a versão correta da biblioteca e navegue até o `ADBMobile.winmd` arquivo.

   Para obter mais informações, consulte o *Selecione a versão correta* abaixo.

1. Clique em **[!UICONTROL Adicionar]**.

1. Verifique se `ADBMobile.winmd` é selecionado no **[!UICONTROL Gerenciador de referência]** e clique em **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Ao adicionar uma referência a um aplicativo do Windows Phone, selecione `ADBMobile.winmd`, altere o filtro de arquivo padrão de **[!UICONTROL Arquivos de componente]** para **Todos os arquivos**.

1. No **[!UICONTROL Explorador de soluções]**, clique com o botão direito do mouse **[!UICONTROL Referências]** e selecione **[!UICONTROL Adicionar referência]**.

   Pule esta etapa se você também tiver um projeto C++ em sua solução.

1. No **Windows** à esquerda, selecione **[!UICONTROL Extensões]**, em seguida, selecione e adicione **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Adicione a seguinte linha à sua classe:

   ```
   using ADBMobile;
   ```

1. Clique com o botão direito do mouse no seu projeto e selecione **[!UICONTROL Adicionar]** > **[!UICONTROL Item existente]**.

1. Navegue até o `ADBMobileConfig.json` e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no `ADBMobileConfig.json` na solução e selecione **[!UICONTROL Propriedades]**.

1. Alterar **[!UICONTROL Ação de build]** para **[!UICONTROL Conteúdo]**.

## Adicionar a biblioteca e o arquivo de configuração ao seu projeto - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie o Visual Studio e abra sua solução.
1. No **[!UICONTROL Explorador de soluções]**, clique com o botão direito do mouse no projeto e selecione **[!UICONTROL Adicionar]** > **[!UICONTROL Referências]**.

1. Selecione a versão correta da biblioteca e adicione uma referência ao `ADBMobile.winmd` arquivo.

   Para obter mais informações, consulte o *Selecione a versão correta* abaixo.

1. Clique em **[!UICONTROL Adicionar]**.

1. No **[!UICONTROL Gerenciador de referência]** verifique se `ADBMobile.winmd` está selecionada e clique em **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Ao adicionar uma referência a um aplicativo do Windows Phone, selecione `ADBMobile.winmd`, altere o filtro de arquivo padrão de **[!UICONTROL Arquivos de componente]** para **Todos os arquivos**.

1. Adicione a seguinte linha à sua classe:

   ```
   using namespace ADMS::Measurement;
   ```

1. Clique com o botão direito do mouse no seu projeto e selecione **[!UICONTROL Adicionar]** > **[!UICONTROL Item existente]**.

1. Navegue até o `ADBMobileConfig.json` e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no `ADBMobileConfig.json` na solução e selecione **[!UICONTROL Propriedades]**.

1. No **[!UICONTROL Geral]** guia, alterar **[!UICONTROL Conteúdo]** para **[!UICONTROL Sim]** e clique em **[!UICONTROL OK]**.

## Adicionar a biblioteca e o arquivo de configuração ao seu projeto - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie o Visual Studio e abra sua solução.
1. No **Explorador de soluções**, clique com o botão direito do mouse **[!UICONTROL Referências]** e selecione **[!UICONTROL Adicionar referência]**.

   Para obter mais informações, consulte *Selecione a versão correta* abaixo.

1. Selecione a versão correta da biblioteca e navegue até o `ADBMobile.winmd` arquivo.

1. Clique em **[!UICONTROL Adicionar]**.

1. Verifique se `ADBMobile.winmd` está marcado no **[!UICONTROL Gerenciador de referência]** e clique em **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Ao adicionar uma referência a um aplicativo do Windows Phone, selecione `ADBMobile.winmd`, altere o filtro de arquivo padrão de **[!UICONTROL Arquivos de componente]** para **Todos os arquivos**.

1. No **[!UICONTROL Explorador de soluções]**, clique com o botão direito do mouse **[!UICONTROL Referências]** e selecione **[!UICONTROL Adicionar referência]**.

   Pule esta etapa se você também tiver um projeto C++ em sua solução.

1. No **[!UICONTROL Windows]** à esquerda, selecione **[!UICONTROL Extensões]** e selecione e adicione **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Clique com o botão direito do mouse no projeto e selecione **[!UICONTROL Adicionar]** > **[!UICONTROL Item existente]**.

1. Navegue até o `ADBMobileConfig.json` e clique em **[!UICONTROL Adicionar]**.

1. Clique com o botão direito do mouse no `ADBMobileConfig.json]` na solução e selecione **[!UICONTROL Propriedades]**.

1. Com **[!UICONTROL Propriedades do arquivo]** selecionado, assegure **[!UICONTROL Ação do pacote]** está definida como **[!UICONTROL Conteúdo]**.

   Para projetos JavaScript, o arquivo é definido como **[!UICONTROL Conteúdo]** por padrão.

## Atualizar o arquivo de configuração ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

O `ADBMobileConfig.json` O arquivo contém as configurações globais do SDK e está localizado na raiz do projeto após concluir as etapas no *Adicionar a biblioteca e o arquivo de configuração ao projeto* seção. Se o seu `ADBMobileConfig.json` O arquivo não foi pré-configurado pelo Adobe Mobile Services, é necessário atualizar alguns valores para começar.

Este é um exemplo de um `ADBMobileConfig.json` arquivo:

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

* **Analytics**: `rsids` e `server`
* **Target**: `clientCode`
* **Gerenciamento de público-alvo**: `server`

Para obter mais detalhes, consulte [Configuração do ADBMobileConfig.json](/help/windows-appstore/c-configuration/methods.md).

## Depuração {#section_3A10376A60394A15BEE483323E0CD4AA}

Quando quiser habilitar a depuração no SDK, é necessário chamar `ADBMobile.Config.setDebugLogging(true);`.

Para aplicativos em C Sharp e JS, é necessário habilitar a depuração de código nativa ao concluir as seguintes etapas (a depuração de código nativa é a configuração padrão para aplicativos em C++):

### C Nitidez

Clique com o botão direito do mouse no projeto e selecione **[!UICONTROL Propriedades]** > **[!UICONTROL Guia Depurar]**. Na lista suspensa do depurador , selecione **[!UICONTROL Somente nativo]**.

### JS

Clique com o botão direito do mouse no projeto e selecione  **[!UICONTROL Propriedades]** > **[!UICONTROL Propriedades da configuração]** > **[!UICONTROL Guia Depurar]**. Altere o menu suspenso do tipo de depurador para **Somente nativo**.

Pronto! Agora você está pronto para implementar o Analytics, o Target e o Gerenciamento de público-alvo no aplicativo Windows 8.1 Universal App Store.
