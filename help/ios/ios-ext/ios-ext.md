---
description: A extensão iOS ajuda a coletar dados de uso dos aplicativos do Apple Watch (WatchOS 1), widgets de hoje, widgets de edição de imagens e outros aplicativos iOS de extensão.
seo-description: A extensão iOS ajuda a coletar dados de uso dos aplicativos do Apple Watch (WatchOS 1), widgets de hoje, widgets de edição de imagens e outros aplicativos iOS de extensão.
seo-title: Implementação de extensão do iOS
solution: Experience Cloud,Analytics
title: Implementação de extensão do iOS
topic: Desenvolvedor e implementação
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
translation-type: ht
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Implementação de extensão do iOS {#ios-extension-implementation}

A extensão iOS ajuda a coletar dados de uso dos aplicativos do Apple Watch (WatchOS 1), widgets de hoje, widgets de edição de imagens e outros aplicativos iOS de extensão.

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Recomendações para usar o SDK do iOS em vez do seu invólucro {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>Recomendamos o uso do SDK do iOS em vez do seu próprio invólucro.

A Apple oferece um conjunto de APIs que permitem a comunicação do aplicativo Watch com o aplicativo contentor, enviando as solicitações para o aplicativo contêiner e recebendo as respostas. Embora você possa enviar dados de rastreamento como um dicionário do aplicativo Watch para o aplicativo que contém a API e depois chamar qualquer método de rastreamento no aplicativo que contém a API para enviar dados, essa solução possui algumas limitações.

Na maioria dos casos quando um usuário está usando o aplicativo Watch, o aplicativo contêiner está sendo executado em segundo plano e só é seguro chamar `TrackActionInBackground`, `TrackLocation`, e `TrackBeacon`. O uso de outros métodos de rastreamento interfere nos dados do ciclo de vida, por isso você deve usar apenas esses três métodos para enviar os dados do aplicativo Watch.

Mesmo que esses três métodos de rastreamento atendam aos seus requisitos, use o SDK do iOS, pois o SDK para o aplicativo Watch inclui todos os recursos Móveis, exceto as mensagens no aplicativo.

## Introdução {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>Certifique-se de ter um projeto com pelo menos os seguintes destinos:
>
>* Um destino para conter o aplicativo.
>* Um destino para a extensão.
>



Se você estiver trabalhando em um aplicativo WatchKit, você deve ter um terceiro destino. Para obter mais informações sobre como desenvolver software para o Apple Watch, consulte [Desenvolvimento para o Apple Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1).

## Configurar o aplicativo contêiner {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

Conclua as seguintes etapas no projeto Xcode:

1. Arraste a pasta AdobeMobileLibrary no seu projeto.
1. Certifique-se de que o arquivo `ADBMobileConfig.json` é um membro do destino do seu aplicativo contêiner.
1. Na guia **[!UICONTROL Criar fases]** do destino do seu aplicativo contêiner, expanda a seção **[!UICONTROL Link binário com bibliotecas]** e adicione as seguintes bibliotecas:

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Abra a guia **[!UICONTROL Recursos]** do destino do aplicativo contêiner, ative **[!UICONTROL Grupos de aplicativos]**, e adicione um novo grupo de aplicativos (por exemplo, `group.com.adobe.testAp`).

1. No delegado do seu aplicativo, defina o grupo de aplicativos em `application:didFinishLaunchingWithOptions` antes de fazer quaisquer interações com a biblioteca do Adobe Mobile:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Verifique se o aplicativo foi criado sem erros inesperados.

## Configurar a extensão {#section_28C994B7892340AC8D1F07AF26FF3946}

1. Certifique-se de que o arquivo `ADBMobileConfig.json` é um membro do destino da sua extensão.
1. Na guia **[!UICONTROL Criar fases]** do destino da sua extensão, expanda a seção **[!UICONTROL Link binário com bibliotecas]** e adicione as seguintes bibliotecas:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Abra a guia **[!UICONTROL Recursos]** do destino da extensão, ative **[!UICONTROL Grupos de aplicativos]** e selecione o grupo de aplicativos que você adicionou na etapa 4 de *Configurar o aplicativo contêiner*, descrita acima.

1. No InterfaceController, defina o grupo de aplicativos em `awakeWithContext:` antes de fazer quaisquer interações com a biblioteca do Adobe Mobile:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Verifique se o aplicativo foi criado sem erros inesperados.

## Observações adicionais {#section_21497E81231549CB9F164DEECFF5BA0D}

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

