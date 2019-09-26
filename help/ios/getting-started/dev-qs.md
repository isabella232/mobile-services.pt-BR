---
description: Esta informação ajuda a implementar a biblioteca do iOS e coletar medições de ciclo de vida, como inicializações, atualizações, sessões, usuários envolvidos e assim por diante.
seo-description: Esta informação ajuda a implementar a biblioteca do iOS e coletar medições de ciclo de vida, como inicializações, atualizações, sessões, usuários envolvidos e assim por diante.
seo-title: Implementação principal e ciclo de vida
solution: Marketing Cloud,Analytics
title: Implementação principal e ciclo de vida
topic: Desenvolvedor e implementação
uuid: 96d06325-e424-4770-8659-4b5431318ee3
translation-type: tm+mt
source-git-commit: be980e0e639d5b0df3f1b6a6f91f3ad0a5efe8d7

---


# Core implementation and lifecycle {#core-implementation-and-lifecycle}

Esta informação ajuda a implementar a biblioteca do iOS e coletar medições de ciclo de vida, como inicializações, atualizações, sessões, usuários envolvidos e assim por diante.

## Baixar o SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>To download the SDKs, you **must** use iOS 6 or later.

**Pré-requisitos**

Antes de baixar o SDK, conclua as etapas em *Criar um conjunto* de relatórios na implementação [principal e no ciclo de vida](/help/ios/getting-started/requirements.md) para configurar um conjunto de relatórios de desenvolvimento e baixar uma versão pré-preenchida do arquivo de configuração.

Para baixar o SDK:

1. Download, unzip the `[Your_App_Name_]AdobeMobileLibrary-4.*-iOS.zip` file and verify that you have the following software components:

   * `ADBMobile.h`, arquivo de cabeçalho em Objective-C usado no AppMeasurement do iOS.
   * `ADBMobileConfig.json`, que é o arquivo de configuração de SDK personalizado para o seu aplicativo.
   * `AdobeMobileLibrary.a`, a bitcode-enabled fat binary that contains the library builds for iOS devices (armv7, armv7s, arm64), and simulators (i386, x86_64).

      Esse binário deve ser vinculado quando o destino for pretendido para um aplicativo do iOS.

   * `AdobeMobileLibrary_Extension.a`, um binário multiarquitetura habilitado para código de bits que contém os builds da biblioteca de dispositivos (armv7, armv7s, arm64) e dos simuladores (i386 e x86_64) do iOS.

      Esse binário deve ser vinculado quando o destino for pretendido para uma extensão do iOS.

   * `AdobeMobileLibrary_Watch.a`, um binário multiarquitetura habilitado para código de bits que contém os builds da biblioteca dos dispositivos (armv7k) e dos simuladores (i386 e x86_64) do Apple Watch.

      Esse binário deve ser vinculado quando o destino for pretendido para um aplicativo de extensão do Apple Watch (watchOS 2).

   * `AdobeMobileLibrary_TV.a`, um binário multiarquitetura habilitado para código de bits que apresenta os builds da biblioteca dos novos dispositivos (arm64) e simuladores (x86_64) da Apple TV.

      Esse binário deve ser vinculado quando o destino for pretendido para um aplicativo da Apple TV (tvOS).

>[!IMPORTANT]
>
>If you download the SDK outside the Adobe Mobile services UI, the `ADBMobileConfig.json` file must be manually configured. If you are new to Analytics and the Mobile SDK, see [Before You Start](/help/ios/getting-started/requirements.md) to set up a development report suite and download a pre-populated version of the configuration file.

## Add the SDK and config file to your project {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Abra o Xcode IDE e o seu aplicativo.
1. No Navegador de projetos, arraste a pasta `AdobeMobileLibrary` e solte-a no seu projeto.
1. Verifique o seguinte:

   * A caixa de seleção **[!UICONTROL Copiar itens se necessário]está marcada.**
   * **[!UICONTROL Criar grupos]** está selecionado.
   * Nenhuma das caixas de seleção na seção **[!UICONTROL Adicionar aos destinos]está marcada.**
   ![](assets/step_3.png)

1. Clique em **[!UICONTROL Concluir]**.
1. In **[!UICONTROL Project Navigator]**, select **[!UICONTROL`ADBMobileConfig.json`]**.
1. In **[!UICONTROL File Inspector]**, add the JSON file to any targets in your project that will use the Adobe SDK.

   ![](assets/step_4.png)

1. In **[!UICONTROL Project Navigator]**, complete the following steps:

   1. Clique no seu aplicativo.
   1. Na guia **[!UICONTROL Geral]**, selecione seus alvos e vincule as estruturas e bibliotecas necessárias nas seções **[!UICONTROL Estruturas vinculadas]e** Bibliotecas **.**
   * **Destinos de aplicativos iOS**
      * `SystemConfiguration.framework`
      * `WebKit.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary.a`
   * **Destino de extensão do iOS**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Extension.a`
   * **Destino Apple Watch (watchOS 2)**

      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Watch.a`
   * **Destino da Apple TV (tvOS)**:

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_TV.a`
   >[!CAUTION]
   >
   > Linking more than one `AdobeMobileLibrary*.a` file in the same target will result in unexpected behavior or the inability to build.

1. Verifique se o aplicativo foi criado sem erros.

## Implement lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

>[!IMPORTANT]
>
>iOS will send lifecycle information with or without calling `collectlifecycledata`, and `collectlifecycledata` is only a way to initiate lifecycle earlier in the application's launch sequence.

After you enable lifecycle, each time your app is launched, one hit is sent to measure launches, upgrades, sessions, engaged users, and other [Lifecycle Metrics](/help/ios/metrics.md).

Adicione uma chamada `collectLifecycleData`/ `collectLifecycleDataWithAdditionalData` em `application:didFinishLaunchingWithOptions`:

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
 [ADBMobile collectLifecycleData]; 
    return YES; 
}
```

### Include additional data with lifecycle calls

Para incluir dados adicionais com chamadas de ciclo de vida, use `collectLifecycleDataWithAdditionalData`:

>[!IMPORTANT]
>
>Any data that is passed to the SDK through `collectLifecycleDataWithAdditionalData:` is persisted in `NSUserDefaults` by the SDK. O SDK desmonta os valores no parâmetro `NSDictionary` que não são dos tipos `NSString` ou `NSNumber`.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
    NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
    [contextData setObject:@"Game" forKey:@"myapp.category"]; 
    [ADBMobile collectLifecycleDataWithAdditionalData:contextData]; 
    return YES; 
}
```

Os valores dos dados de contexto adicionais enviados com o `collectLifecycleDataWithAdditionalData` devem ser mapeados para variáveis personalizadas no Adobe Mobile Services:

![](assets/map-variable-lifecycle.png)

As outras medições de ciclo de vida são coletadas automaticamente. Para obter mais informações, consulte [Medições de ciclo de vida](/help/ios/metrics.md).

## O que fazer em seguida {#section_A24DC703359D4B5C8F493D6421306FD3}

Conclua as seguintes tarefas:

* [Rastrear estados do aplicativo](/help/ios/analytics-main/states.md)
* [Rastrear ações do aplicativo](/help/ios/analytics-main/actions.md)
