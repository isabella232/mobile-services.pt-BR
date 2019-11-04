---
description: Estes são os métodos do Adobe Experience Platform Identity Service fornecidos pela biblioteca do iOS.
seo-description: Estes são os métodos do Adobe Experience Platform Identity Service fornecidos pela biblioteca do iOS.
seo-title: Métodos do Adobe Experience Platform Identity Service
solution: Experience Cloud,Analytics
title: Métodos do Adobe Experience Platform Identity Service
topic: Desenvolvedor e implementação
uuid: cdd307bc-8b7d-47a8-b77e-00902b9e2968
translation-type: ht
source-git-commit: cbbb85b4d117fcaa502a1e01423f1f5d3b2ecc2b

---


# Métodos do Adobe Experience Platform Identity Service {#experience-cloud-id-service-methods}

Estes são os métodos do Adobe Experience Platform Identity Service fornecidos pela biblioteca do iOS.

O SDK oferece suporte a várias soluções da Adobe Experience Cloud no momento, como o Analytics, o Target, o Audience Manager e o serviço de ID de visitante da Experience Cloud.

Métodos recebem o prefixo de acordo com a solução, e os métodos da Experience Cloud ID recebem o prefixo `visitor`. Para obter mais informações, consulte [Habilitar a Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).

* **`+`(nullable NSURL`*`)visitorAppendToURL:(nullable NSURL`*`)url;**

   Acrescenta dados de visitantes da Adobe a uma cadeia de caracteres de URL para uso com a biblioteca JavaScript da Adobe. Para usar este método, você deve ter o SDK móvel versão 4.12 ou posterior. Para obter mais informações, consulte [Anexar função de ajuda da ID de visitante](https://marketing.adobe.com/resources/help/pt_BR/mcvid/mcvid-appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Este método pode causar uma chamada de rede de bloqueio. Não chame este método em tópicos sensíveis ao tempo.

   * Entrada: `URL<NSURL>`
Uma cadeia de caracteres de URL necessária, à qual a informação do visitante será anexada.
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
      >Este método pode causar uma chamada de bloqueio de rede e **não** deve ser chamado de um encadeamento da interface do usuário.

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

   Sincroniza o tipo de identificador e o valor fornecidos ao serviço de ID. Transmite no `authState` um dos seguintes valores:

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

* **visitorgetUrlVariablesAsync**

   Introduzido na versão 4.16.0, este método retorna uma sequência de caracteres devidamente formada que contém variáveis de URL do Serviço de ID de visitante. Para obter mais informações sobre como esse método é usado, consulte [Métodos do Adobe Experience Platform Identity Service](/help/ios/reference/hybrid-app.md).

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

