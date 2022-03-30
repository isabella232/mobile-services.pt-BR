---
description: Esta é uma lista de métodos fornecidos pela biblioteca do iOS.
solution: Experience Cloud Services,Analytics
title: Métodos de configuração
topic-fix: Developer and implementation
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
exl-id: b6841808-8fa8-4090-8cb3-ce647a3d5d08
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 100%

---

# Métodos de configuração {#configuration-methods}

Esta é uma lista de métodos fornecidos pela biblioteca do iOS.

Atualmente, o SDK é compatível com várias soluções da Adobe Experience Cloud, como o Analytics, o Target, o Audience Manager e o Adobe Experience Platform Identity Service.

* **setAppExtensionType**

   Define a configuração do SDK do Adobe Mobile para determinar que tipo de extensão está sendo executada no momento.

   É definido como um dos valores abaixo:
   * `ADBMobileAppExtensionTypeRegular` - a extensão é fornecida com um aplicativo contêiner.
   * `ADBMobileAppExtensionTypeStandAlone` - a extensão não é fornecida com um aplicativo contêiner.

   >[!TIP]
   >
   >Este método **só** deve ser usado se o aplicativo tiver uma extensão ou for uma extensão independente. Para obter mais informações, consulte *ADBMobileAppExtensionType* abaixo.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **versão**

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

   Define o de privacidade do usuário atual como `status` status.

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

   Retorna o identificador de visitante gerado automaticamente. Esta é um identificador de visitante único específico do aplicativo gerado pelos servidores da Adobe. Se não for possível atingir a geração de servidores no momento, a ID será gerada usando a CFUUID da Apple. O valor é gerado na primeira inicialização e é armazenado e usado a partir desse ponto. Essa ID é preservada entre as atualizações do aplicativo, é salva e restaurada durante o processo padrão de backup do aplicativo e é removida na desinstalação.

   >[!TIP]
   >
   >Se seu aplicativo for atualizado do SDK 3.x da Experience Cloud para o 4.x, a ID anterior de visitante, personalizada ou gerada automaticamente, será recuperada e armazenada como o identificador personalizado do usuário. Para obter mais informações, consulte a linha `userIdentifier` abaixo. Isso preserva os dados dos visitantes entre as atualizações de SDK. Para novas instalações no SDK 4.x, o identificador do usuário é `nil` e o identificador de rastreamento é usado.

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
   >Se seu aplicativo for atualizado do SDK 3.x da Experience Cloud para o 4.x, a ID anterior de visitante, personalizada ou gerada automaticamente, será recuperada e armazenada como o identificador personalizado do usuário. Isso preserva os dados do visitante entre as atualizações de SDK.

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
   >Este método é destinado a aplicativos que realizam registros para receber notificações quando são executados em segundo plano e só deve ser chamado a partir do código executado enquanto o aplicativo está em segundo plano.

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
   >A localização preferida para invocar este método está em `application:didFinishLaunchingWithOptions:`.

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

   Este método deve ser chamado do ponto de entrada do seu aplicativo. Sempre que aplicável, isso pode incluir um ou ambos os métodos: `application:didFinishLaunchingWithOptions:` e/ou `applicationWillEnterForeground:` na classe AppDelegate.

   >[!IMPORTANT]
   >
   >Os dados passados para o SDK por meio do `collectLifecycleDataWithAdditionalData:` persistirão no SDK em `NSUserDefaults`. O SDK eliminará quaisquer valores no parâmetro `NSDictionary` que não sejam do tipo `NSString` ou `NSNumber`. Para usar o `collectLifecycleDataWithAdditionalData:`, você deve ter a **versão 4.4** ou posterior do SDK.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **pauseCollectingLifecycleData**

   Use esta API para pausar a coleta de dados do ciclo de vida. Para obter mais informações, consulte [Medições de ciclo de vida](/help/ios/metrics.md).

   >[!IMPORTANT]
   >
   >No método delegado do `applicationDidEnterBackground`, você deve chamar primeiro o método `pauseCollectingLifecycleData`.
   >
   >A API é fornecida para atenuar o problema no iPhone 7/7s ou em dispositivos mais antigos com o iOS 13, em que a métrica de duração da sessão ficou anormal. Isso se deve a algumas alterações desconhecidas que ocorreram no iOS 13, onde o iOS não deixa tempo suficiente para que a tarefa em segundo plano seja concluída quando você cria o aplicativo em segundo plano.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) pauseCollectingLifecycleData;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      - (void)applicationDidEnterBackground:(UIApplication *)application{
          // manually stop the lifecycle of SDK
          // important: do NOT call any track state or track action after this line
          [ADBMobile pauseCollectingLifecycleData];   
      
      
          // the following code is optional, may help to mitigate the issue a bit more. If you have other logic to run here that probably takes more than 10ms, then there is no need to add this line of code.
          [NSThread sleepForTimeInterval:0.01];
      
      
          // app's code to handle applicationDidEnterBackground
      }
      ```


* **overrideConfigPath**

   Permite carregar um arquivo de configuração JSON do ADBMobile diferente quando o aplicativo é iniciado. A configuração diferente é utilizada até o aplicativo ser fechado.

   >[!IMPORTANT]
   >
   >Para usar o `overrideConfigPath`, você deve ter a versão 4.2 ou posterior do SDK.

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
   >Este método só deve ser usado no método `application:didRegisterForRemoteNotificationsWithDeviceToken:`.

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

   Define o IDFA no SDK. Se o IDFA tiver sido definido no SDK, o IDFA será enviado no ciclo de vida. Ele também pode ser acessado em Sinais (Postbacks).

   >[!TIP]
   >
   >Recupere a IDFA das APIs da Apple **só** se você estiver usando um serviço de anúncios. Se você recuperar o IDFA e não o utilizar corretamente, seu aplicativo poderá ser rejeitado.
   >
   >Se seu aplicativo exigir o IDFA, verifique a [documentação da Apple](https://developer.apple.com/documentation/adsupport) para consultar as preferências do usuário no Rastreamento de anúncio e recuperar o valor do IDFA.
   >
   >Para iOS 14+, a nova [Estrutura de transparência de rastreamento de aplicativos](https://developer.apple.com/documentation/apptrackingtransparency) precisa ser implementada para recuperar o valor do IDFA.
   * Esta é a sintaxe para este método:

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSString *idfa = // retrieve IDFA using AdSupport (before iOS 14.0) and/or AppTrackingTransparency (iOS 14.0+)
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
