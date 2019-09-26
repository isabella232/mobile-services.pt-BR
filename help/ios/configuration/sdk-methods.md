---
description: Esta é uma lista de métodos fornecidos pela biblioteca do iOS.
seo-description: Esta é uma lista de métodos fornecidos pela biblioteca do iOS.
seo-title: Métodos de configuração
solution: Marketing Cloud,Analytics
title: Métodos de configuração
topic: Desenvolvedor e implementação
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Configuration methods {#configuration-methods}

Esta é uma lista de métodos fornecidos pela biblioteca do iOS.

O SDK suporta atualmente várias Soluções da Adobe Experience Cloud, incluindo o Analytics, o Target, o Audience Manager e o Adobe Experience Platform Identity Service.

* **setAppExtensionType**

   Define a configuração do SDK do Adobe Mobile para determinar que tipo de extensão está sendo executada atualmente.

   É definido como um dos valores abaixo:
   * `ADBMobileAppExtensionTypeRegular` - a extensão é fornecida com um aplicativo contêiner.
   * `ADBMobileAppExtensionTypeStandAlone` - a extensão não é fornecida com um aplicativo contêiner.
   >[!TIP]
   >
   >This method should **only** be used if your app has an extension or is a stand-alone extension. For more information, see *ADBMobileAppExtensionType* below.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **version**

   Retorna a versão atual da biblioteca do Adobe Mobile.

   * Esta é a sintaxe para este método:

      ```objective-c
      +(NSString*) version;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSString*libraryVersion = [ADBMobileversion];
      ```

* **privacyStatus**

   Retorna a representação de enumeração do status de privacidade do usuário atual:

   * `ADBMobilePrivacyStatusOptIn` - as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut` - as ocorrências serão descartadas.
   * `ADBMobilePrivacyStatusUnknown` - se o rastreamento offline estiver ativado, as ocorrências são salvas até o status de privacidade ser alterado para aceitar (e então as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o rastreamento offline não estiver ativado, as ocorrências são descartadas até o status de privacidade ser alterado parar aceitar.
O valor padrão está definido no arquivo `ADBMobileConfig.json`.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (ADBMobilePrivacyStatus) privacyStatus;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobilePrivacyStatus privacyStatus = [ADBMobileprivacyStatus];
      ```

* **setPrivacyStatus**

   Define o de privacidade do usuário atual como `status`status.

   É definido como um dos valores abaixo:

   * `ADBMobilePrivacyStatusOptIn` - as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut` - as ocorrências serão descartadas.
   * `ADBMobilePrivacyStatusUnknown` - se o rastreamento offline estiver ativado, as ocorrências são salvas até o status de privacidade ser alterado para aceitar (e então as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o rastreamento offline não estiver ativado, as ocorrências são descartadas até o status de privacidade ser alterado parar aceitar.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) setPrivacyStatus:(ADBMobilePrivacyStatus)status;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn];
      ```

* **lifetimeValue**

   Retorna o valor do tempo de vida do usuário atual. O valor padrão é `0`.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (NSDecimalNumber *) lifetimeValue;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSDecimalNumber *lifeValue = [ADBMobile lifetimeValue];
      ```

* **trackingIdentifier**

   Retorna o identificador de visitante gerado automaticamente. Esta é uma ID de visitante único específica do aplicativo, gerada pelos servidores da Adobe. Se os servidores da Adobe não puderem ser alcançados no momento da geração, a ID será gerada por meio do CFUUID da Apple. O valor é gerado na primeira inicialização e é armazenado e usado a partir desse ponto. Essa ID é preservada entre as atualizações do aplicativo, é salva e restaurada durante o processo padrão de backup do aplicativo e é removida durante a desinstalação.

   >[!TIP]
   >
   >Se seu aplicativo for atualizado do Experience Cloud 3.x para o SDK 4.x, a ID de visitante personalizada ou gerada automaticamente anterior será recuperada e armazenada como o identificador de usuário personalizado. Para obter mais informações, consulte a linha `userIdentifier` abaixo. Isso preserva os dados dos visitantes entre as atualizações de SDK. Para novas instalações no SDK 4.x, o identificador do usuário é `nil` e o identificador de rastreamento é usado.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (NSString *) trackingIdentifier;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSString *tid = [ADBMobile trackingIdentifier];
      ```

* **userIdentifier**

   Se um identificador do usuário foi definido, ele é retornado. Caso contrário, `nil` é retornado. O valor padrão é `nil`.

   >[!TIP]
   >
   >Se seu aplicativo for atualizado do SDK 3.x da Experience Cloud para o 4.x, a ID de visitante personalizada ou gerada automaticamente anterior será recuperada e armazenada como o identificador de usuário personalizado. Isso preserva os dados do visitante entre as atualizações de SDK.

   Para novas instalações do SDK 4.x, o identificador do usuário é `nil` até que seja definido.

   * Esta é a sintaxe para este método:

      ```objective-c
      +(NSString *) userIdentifier;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSString *uid = [ADBMobileuserIdentifier];
      ```

* **setUserIdentifier**

   Define o identificador do usuário para `identifier`.

   * Esta é a sintaxe para este método:

      ```objective-c
      +(void)setUserIdentifier:(NSString*)identifier;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile setUserIdentifier:@"billybob"]; 
      ```

* **debugLogging**

   Retorna a preferência de log para a depuração atual. O valor padrão é `NO`.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (BOOL) debugLogging;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      BOOL debugging = [ADBMobile debugLogging];
      ```

* **setDebugLogging**

   Define a preferência do log de depuração como `debug`.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) setDebugLogging:(BOOL)debug;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile setDebugLogging:YES];
      ```

* **keepLifecycleSessionAlive**

   Indica ao SDK que o próximo resumo em segundo plano não deve iniciar uma nova sessão, independentemente do tempo limite de valor da sessão do ciclo de vida presente no arquivo de configuração.

   >[!TIP]
   >
   >Este método é destinado a aplicativos que se registram para receber notificações enquanto estão em segundo plano e só deve ser chamado a partir do código executado enquanto o aplicativo está em segundo plano.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) keepLifecycleSessionAlive;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile keepLifecycleSessionAlive]; 
      ```

* **collectLifecycleData**

   Indica ao SDK que os dados do ciclo de vida devem ser coletados para uso em todas as soluções no SDK. Para obter mais informações, consulte [Medições de ciclo de vida](/help/ios/metrics.md).

   >[!TIP]
   >
   >The preferred location to invoke this method is in `application:didFinishLaunchingWithOptions:`.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) collectLifecycleData;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile collectLifecycleData];
      ```

* **collectLifecycleDataWithAdditionalData:**

   Permite que você envie dados adicionais ao coletar medições de ciclo de vida.

   Esse método deve ser chamado a partir do ponto de entrada do aplicativo. Where applicable, this may include one or both of the methods `application:didFinishLaunchingWithOptions:` and/or `applicationWillEnterForeground:` in your AppDelegate class.

   >[!IMPORTANT]
   >
   >Data that is passed to the SDK via `collectLifecycleDataWithAdditionalData:` will be persisted by the SDK in `NSUserDefaults`. O SDK eliminará quaisquer valores no parâmetro `NSDictionary` que não sejam do tipo `NSString` ou `NSNumber`. To use  `collectLifecycleDataWithAdditionalData:`, you must have SDK **version 4.4** or later.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **overrideConfigPath**

   Permite carregar um arquivo de configuração JSON do ADBMobile diferente ao iniciar o aplicativo. A configuração diferente é utilizada até o aplicativo ser fechado.

   >[!IMPORTANT]
   >
   >To use `overrideConfigPath`, you must have SDK version 4.2 or later.

   * Esta é a sintaxe para este método:

      ```objective-c
       + (void) overrideConfigPath: (nullableNSString *) path;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
      [ADBMobile overrideConfigPath:filePath];
      ```

* **setPushIdentifier**

   Define o token do dispositivo para notificações por push.

   >[!IMPORTANT]
   >
   >This method should only be used in the  `application:didRegisterForRemoteNotificationsWithDeviceToken:` method.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) setPushIdentifier:(NSData *)deviceToken;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      - (void) application:(UIApplication *) application  didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
      [ADBMobile setPushIdentifier:deviceToken];  
      }
      ```

* **setAdvertisingIdentifier**

   Define o IDFA no SDK. Se a IDFA for definida no SDK, ela será enviada no ciclo de vida. Também pode ser acessado em Sinais (Postbacks).

   >[!TIP]
   >
   >Retrieve the IDFA from Apple APIs **only** if you are using an ad service. Se você recuperar o IDFA e não o utilizar corretamente, seu aplicativo poderá ser rejeitado.

   * Esta é a sintaxe para este método:

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSString *idfa = [[[ASIdentifierManager sharedManager]advertisingIdentifier] UUIDString]; 
      [ADBMobile setAdvertisingIdentifier:idfa]; 
      ```

## ADBMobileAppExtensionType enum {#section_18DB491D0ABC4765BB5A467D8FEF4F1B}

```objective-c
/** 
 * @brief An enum type. 
 * The possible types of app extension you might use 
 * @see setAppExtensionType 
 */ 
typedef NS_ENUM(NSUInteger, ADBMobileAppExtensionType) { 
    ADBMobileAppExtensionTypeRegular = 0, /*!< Enum value ADBMobileAppExtensionTypeRegular. */ 
    ADBMobileAppExtensionTypeStandAlone = 1 /*!< Enum value ADBMobileAppExtensionTypeStandAlone. */ 
};
```

