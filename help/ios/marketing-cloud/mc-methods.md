---
description: Estes são os métodos do Adobe Experience Platform Identity Service fornecidos pela biblioteca do iOS.
seo-description: Estes são os métodos do Adobe Experience Platform Identity Service fornecidos pela biblioteca do iOS.
seo-title: Métodos do Serviço de identidade da Adobe Experience Platform
solution: Marketing Cloud, Analytics
title: Métodos do Serviço de identidade da Adobe Experience Platform
topic: Desenvolvedor e implementação
uuid: cdd 307 bc -8 b 7 d -47 a 8-b 77 e -00902 b 9 e 2968
translation-type: tm+mt
source-git-commit: cbbb85b4d117fcaa502a1e01423f1f5d3b2ecc2b

---


# Métodos do Serviço de identidade da Adobe Experience Platform {#experience-cloud-id-service-methods}

Estes são os métodos do Adobe Experience Platform Identity Service fornecidos pela biblioteca do iOS.

O SDK oferece suporte a várias soluções da Adobe Experience Cloud no momento, como o Analytics, o Target, o Audience Manager e o serviço de ID de visitante da Experience Cloud.

Methods are prefixed according to the solution, and Experience Cloud ID methods are prefixed with `visitor`. Para obter mais informações, consulte [Habilitar a Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).

* **`+`(nullable NSURL`*`) visitorappendtourl: (nullable NSURL`*`) url;**

   Acrescenta dados de visitantes da Adobe a uma cadeia de caracteres de URL para uso com a biblioteca JavaScript da Adobe. Para usar este método, você deve ter o Mobile SDK versão 4.12 ou superior. Para obter mais informações, consulte [Anexar função de ajuda da ID de visitante](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Este método pode causar uma chamada de rede de bloqueio. Não chame este método em tópicos sensíveis ao tempo.

   * Input: `URL<NSURL>`
A required URL string that the visitor information will be appended to.
   * `URL<NSURL>`
Cadeia de caracteres com as informações do visitante anexadas.

   * Esta é a amostra de código para este método:

      ```objective-c
       NSURL *url = [NSURL URLWithString:@"https://www.example.com"];  
       NSURL *decoratedURL = [ADBMobile visitorAppendToURL: url];  
       [[UIApplication sharedApplication] openURL: decoratedURL];  
      ```

* **visitorMarketingCloudID**

   Recupera a Experience Cloud ID a partir do serviço de ID.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (NSString  *)  visitorMarketingCloudID;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSString *mcid = [ADBMobile visitorMarketingCloudID]; 
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **visitorSyncIdentifiers:**

   Com a Experience Cloud ID, é possível definir IDs adicionais de clientes que podem ser associadas a cada visitante. A API de visitante aceita várias IDs do cliente para o mesmo visitante, juntamente com um identificador de tipo de cliente para separar o escopo de diferentes IDs do cliente. Este método corresponde a `setCustomerIDs` na biblioteca do JavaScript.

   * Esta é a sintaxe para este método:

      ```objective-c
      +  (void)  visitorSyncIdentifiers:(NSDictionary  *)identifiers;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"idType":@"idValue"}];
      ```

* **visitorSyncIdentifiers:authenticationState:**

   Sincroniza os identificadores fornecidos ao serviço de ID. Transmite `authState` como um dos seguintes valores:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * Esta é a sintaxe para este método:

      ```objective-c
      +  (void) visitorSyncIdentifiers:(nullable NSDictionary  *)identifiers  authenticationState:(ADBMobileVisitorAuthenticationState)authState; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"myIdType":@"valueForUser"}  authenticationState:ADBMobileVisitorAuthenticationStateAuthenticated]; 
      ```

* **visitorSyncIdentifierWithType:identifier:authenticationState:**

   Sincroniza o tipo de identificador e o valor fornecidos ao serviço de ID. Pass in the `authState` one of the following values:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) visitorSyncIdentifierWithType:(nullable NSString *)identifierType  
      identifier:(nullable NSString *)identifier authenticationState:
      (ADBMobileVisitorAuthenticationState)authState; 
      ```

   * Esta é a sintaxe para este método:

      ```objective-c
      [ADBMobile visitorSyncIdentifierWithType:@"myIdType" identifier:@"valueForUser"  
      authenticationState:ADBMobileVisitorAuthenticationStateLoggedOut]; 
      ```

* **visitorGetIDs**

   Obtém uma matriz de objetos `ADBVisitorID` somente leitura.

   * Esta é a sintaxe para este método:

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **Visitorgeturlvariablesasync**

   Introduzido na versão 4.16.0, este método retorna uma string formada adequadamente que contém variáveis de URL do serviço de ID do visitante. Para obter mais informações sobre como esse método é usado, consulte [Métodos do Serviço de identidade da Adobe Experience Platform](/help/ios/reference/hybrid-app.md).

   * Esta é a sintaxe para este método:

      ```objectivec
      + (void) visitorGetUrlVariablesAsync:(nullable void (^)(NSString* __nullable urlVariables))callback;
      ```

   * Esta é a amostra de código para este método:

      ```objectivec
      NSString *urlString = @"https://www.mydomain.com/index.php"; 
      [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
        NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
        // use urlStringWithVisitorData 
      }];
      ```

## Interface ADBVisitorID {#section_2FF74454D25C4ADABAC5E43CBFAAEC26}

**Métodos públicos:**

```objective-c
- (nullable NSString *) idType; 
- (nullable NSString *) identifier; 
- (ADBMobileVisitorAuthenticationState) authenticationState; 
```

## ADBMobileVisitorAuthenticationState enum {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```

