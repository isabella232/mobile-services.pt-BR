---
description: A extensão iOS ajuda a coletar dados de uso dos aplicativos do Apple Watch (WatchOS 1), widgets de hoje, widgets de edição de imagens e outros aplicativos iOS de extensão.
seo-description: A extensão iOS ajuda a coletar dados de uso dos aplicativos do Apple Watch (WatchOS 1), widgets de hoje, widgets de edição de imagens e outros aplicativos iOS de extensão.
seo-title: Implementação de extensão do iOS
solution: Marketing Cloud,Analytics
title: Implementação de extensão do iOS
topic: Desenvolvedor e implementação
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# iOS extension implementation {#ios-extension-implementation}

A extensão iOS ajuda a coletar dados de uso dos aplicativos do Apple Watch (WatchOS 1), widgets de hoje, widgets de edição de imagens e outros aplicativos iOS de extensão.

## Nova versão do SDK da Adobe Experience Cloud

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para começar, acesse o Launch.
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Para obter mais informações, consulte [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

## Recommendations for using the iOS SDK instead of your wrapper {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>Recomendamos que você use o SDK do iOS em vez do invólucro.

A Apple oferece um conjunto de APIs que permitem a comunicação do aplicativo Watch com o aplicativo contentor, enviando as solicitações para o aplicativo contêiner e recebendo as respostas. Embora você possa enviar dados de rastreamento como um dicionário do aplicativo Watch para o aplicativo que contém a API e depois chamar qualquer método de rastreamento no aplicativo que contém a API para enviar dados, essa solução possui algumas limitações.

In most cases when a user is using the Watch app, the containing app is running in the background, and it is only safe to call `TrackActionInBackground`, `TrackLocation`, and `TrackBeacon`. O uso de outros métodos de rastreamento interfere nos dados do ciclo de vida, por isso você deve usar apenas esses três métodos para enviar os dados do aplicativo Watch.

Mesmo que esses três métodos de rastreamento atendam aos seus requisitos, use o SDK do iOS, pois o SDK para o aplicativo Watch inclui todos os recursos Móveis, exceto as mensagens no aplicativo.

## Introdução {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>Ensure that you have a project with at least the following targets:
>
>* Um destino para conter o aplicativo.
>* Um destino para a extensão.
>



Se você estiver trabalhando em um aplicativo WatchKit, você deve ter um terceiro destino. For more information on developing for Apple Watch, see Developing for Apple Watch.[](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1)

## Configure the containing app {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

Conclua as seguintes etapas no projeto Xcode:

1. Arraste a pasta AdobeMobileLibrary no seu projeto.
1. Ensure that the `ADBMobileConfig.json` file is a member of the containing app's target.
1. Na guia **[!UICONTROL Criar fases]** do destino do seu aplicativo contêiner, expanda a seção **Link binário com bibliotecas]e adicione as seguintes bibliotecas:[!UICONTROL **

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open the **[!UICONTROL Capabilities]** tab of the containing app's target, enable **[!UICONTROL App Groups]**, and add a new app group (for example, `group.com.adobe.testAp`).

1. No delegado do seu aplicativo, defina o grupo de aplicativos em `application:didFinishLaunchingWithOptions` antes de fazer quaisquer interações com a biblioteca do Adobe Mobile:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Verifique se o aplicativo foi criado sem erros inesperados.

## Configurar a extensão {#section_28C994B7892340AC8D1F07AF26FF3946}

1. Ensure that the `ADBMobileConfig.json` file is a member of the extension's target.
1. Na guia **[!UICONTROL Criar fases]** do destino da sua extensão, expanda a seção **Link binário com bibliotecas]e adicione as seguintes bibliotecas:[!UICONTROL **

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open the **[!UICONTROL Capabilities]** tab of the extension's target, enable **[!UICONTROL App Groups]**, and select the app group that you added in step 4 of *Configuring the Containing App* above.

1. In your InterfaceController, set the app group in `awakeWithContext:` before making any other interactions with the Adobe Mobile library:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Verifique se o aplicativo foi criado sem erros inesperados.

## Additional notes {#section_21497E81231549CB9F164DEECFF5BA0D}

Algumas informações a lembrar:

* Um valor de dados de contexto adicional, `a.RunMode`, foi adicionado para indicar se os dados são provenientes do aplicativo contêiner ou da extensão:

   * `a.RunMode = Application`

      Esse valor significa que a ocorrência veio do aplicativo contêiner.
   * `a.RunMode = Extension`

      Esse valor significa que a ocorrência veio da extensão.

* Se você atualizar de uma versão mais antiga do SDK, quando o aplicativo contentor for iniciado, a Adobe migra automaticamente todos os padrões do usuário e arquivos em cache da pasta do aplicativo contêiner para a pasta compartilhada do grupo de aplicativos.
* Se o aplicativo contentor nunca for inicializado, as ocorrências da extensão serão descartadas.
* O número da versão e o número do build devem ser os mesmos entre o aplicativo contêiner e o aplicativo de extensão.
* Nenhuma chamada de ciclo de vida é acionada em aplicativos de extensão iOS.

