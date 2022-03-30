---
description: Esta é uma lista de métodos do Adobe Target fornecidos pela biblioteca do iOS.
solution: Experience Cloud Services,Analytics
title: Métodos do Target para iOS
topic-fix: Developer and implementation
uuid: 692bcda1-02ba-4902-bd65-15888adf1952
exl-id: ba03f865-970c-4b48-af35-749f05b273d8
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 95%

---

# Métodos do Target para iOS {#target-methods}

Esta é uma lista de métodos do Adobe Target fornecidos pela biblioteca do iOS.

Atualmente, o SDK é compatível com várias soluções da Adobe Experience Cloud, como o Analytics, o Target, o Audience Manager e o Adobe Experience Platform Identity Service. Os métodos apresentam prefixos de acordo com a solução. Por exemplo, os métodos do têm o prefixo `target` target.

>[!TIP]
>
>Medições de ciclo de vida são enviadas como parâmetros para cada carregamento de mbox. Para obter mais informações, consulte [Medições de ciclo de vida](/help/ios/metrics.md). Se você estiver enviando solicitações do Target dentro do método delegado `didFinishLaunching`, adicione uma chamada `[ADBMobile trackAction:data:]` ou `[ADBMobile trackState:data:]` antes do código de implementação do Target. Dessa forma, as solicitações do Target conterão os dados completos do ciclo de vida.

## Referência de classe: ADBTargetLocationRequest

### Propriedades

```objective-c
NSString *name; 
NSString *defaultContent; 
NSMutableDictionary *parameters;
```

### Constantes da cadeia de caracteres

>[!TIP]
>
>As constantes seguintes facilitam o uso ao configurar as chaves para parâmetros personalizados.

```iOS
NSString *const ADBTargetParameterOrderId; 
NSString *const ADBTargetParameterOrderTotal; 
NSString *const ADBTargetParameterProductPurchasedId; 
NSString *const ADBTargetParameterCategoryId; 
NSString *const ADBTargetParameterMbox3rdPartyId; 
NSString *const ADBTargetParameterMboxPageValue; 
NSString *const ADBTargetParameterMboxPc; 
NSString *const ADBTargetParameterMboxSessionId; 
NSString *const ADBTargetParameterMboxHost;
```

>[!IMPORTANT]
>
>* Se você estiver usando SDKs **anteriores** à versão 4.14.0, consulte [Parâmetros de entrada](https://developers.adobetarget.com/api/#input-parameters) para limitações de parâmetros.
>
>* Se você estiver usando a versão 4.14.0 **ou posterior** dos SDKs, consulte [Parâmetros de entrada de lotes](https://developers.adobetarget.com/api/#batch-input-parameters) para limitações de parâmetros.


### Métodos

* **targetLoadRequest:&#x200B;callback**

   Envia request para o servidor do Target configurado e retorna o valor da cadeia de caracteres da oferta gerada em um `callback` de bloqueio.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) targetLoadRequest:(ADBTargetLocationRequest *)request
                        callback:(void (^)(NSString *content))callback;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile targetLoadRequest:myRequest
                          callback:^(NSString *content) {
                            // do something with content
                          }];
      ```

* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:requestLocationParameters:retorno de chamada:**

   Envia uma solicitação para o servidor do Target configurado e retorna o valor da cadeia de caracteres da oferta gerada em um retorno de chamada.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                requestLocationParameters:(nullable NSDictionary *)requestLocationParameters
                                 callback:(nullable void (^)(NSString
                                 * __nullable content))callback;
      ```

   * Retorna: N/A

   * Estes são os parâmetros para este método:

      * **`name`**

         Nome da mbox/localização do Target que você quer recuperar.

         * **Tipo**: NSString*
      * **`defaultContent`**

         O valor retornado no retorno de chamada se não for possível alcançar o servidor do Target, ou se o usuário não estiver qualificado para a campanha.

         * **Tipo**: NSString*
      * **`profileParameters`**

         Os valores neste dicionário serão adicionados ao objeto &quot;profileParameters&quot; na solicitação para o Target.

         * **Tipo**: NSDictionary*
      * **`orderParameters`**

         Os valores neste dicionário serão adicionados ao objeto &quot;order&quot; na solicitação para o Target.

         * **Tipo**: NSDictionary
      * **`mboxParameters`**

         Os valores neste dicionário serão adicionados ao objeto &quot;mboxParameters&quot; na solicitação para o Target.

         * **Tipo**: NSDictionary*
      * **`requestLocationParameters`**

         Os valores neste dicionário serão adicionados ao objeto &quot;requestLocation&quot; na solicitação para o Target.

         **Tipo**: NSDictionary*

      * **`callback`**

         Este método será chamado com o conteúdo da oferta do servidor Target. Se o servidor Target estiver inacessível, ou o usuário não se qualificar para a campanha, defaultContent será retornado.
      **Tipo**: função

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"myHeroBanner"
                            defaultContent:@"defaultHeroBanner.png"
                        profileParameters:@{@"age":@"20-29"}
                          orderParameters:nil
                           mboxParameters:@{@"customParam":@"customValue"}
                requestLocationParameters:@{@"host":@"my.hostname.com"}
                                 callback:^(NSString *content){
                                   // do something with content
                                   myImageView.image = [UIImage imageNamed:content];
                                 }];
      ```

      Para obter mais informações sobre a API subjacente do Target, consulte [Referência da API do Target](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-target/target-api-reference-deprecated).







* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:callback**

   Envia a solicitação para o servidor do Target configurado e retorna o valor da cadeia de caracteres da oferta gerada em um retorno de chamada de bloqueio.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                               callback:(nullable void (^)(NSString * __nullable content))callback;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"mboxName"
                            defaultContent:@"defaultContent"
                         profileParameters:{@"profile-parameter-key": @"profile-parameter-value"}
                           orderParameters:@{@"order-parameter-key": @"order-parameter-value"}
                            mboxParameters:@{@"mbox-parameter-key": @"mbox-parameter-value"}
                                   callback:^(NSString * content) {
                                           //do something with content 
                                 }
                               }];
      ```

* **targetCreateOrder&#x200B;ConfirmRequestWithName:&#x200B;orderId:&#x200B;orderTotal:&#x200B;productPurchasedId:&#x200B;parameters**

   Cria um `ADBTargetLocationRequest`.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateOrderConfirmRequestWithName:(NSString *)name
                                      orderId:(NSString *)orderId
                                  orderTotal:(NSString *)orderTotal
                          productPurchasedId:(NSString *)productPurchasedId
                              parameters:(NSDictionary *)parameters;
      ```

* **targetCreateRequestWithName:&#x200B;&#x200B;defaultContent:&#x200B;parameters**

   O construtor de conveniência cria um objeto ADBTargetLocationRequest com os parâmetros em questão.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateRequestWithName:(NSString *)name
                           defaultContent:(NSString *)defaultContent
                               parameters:(NSDictionary *)parameters;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBTargetLocationRequest *myRequest =  
      [ADBMobile targetCreateRequestWithName:@"heroBanner"
                              defaultContent:@"default.png"
                                  parameters:nil];
      ```

* **targetThirdPartyID**

   Retorna a ID de terceiros.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (nullable NSString *) targetThirdPartyID;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSString *thirdPartyId = [ADBMobile targetThirdPartyID];
      ```

* **targetSetThirdPartyID**

   Define a ID de terceiros.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) targetSetThirdPartyID:(nullable NSString *)thirdPartyID;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile targetSetThirdPartyID:@"thirdPartyID"];
      ```

* **targetClearCookies**

   Apaga quaisquer cookies de destino do seu aplicativo.

   >[!TIP]
   >
   >Desde a versão 4.10.0 do SDK, o Target não usa mais cookies. Esse método redefine thirdPartyID e sessionID.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) targetClearCookies;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile targetClearCookies];
      ```

* **targetPcID**

   Retorna a PcID.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSString *myTargetPcID = [ADBMobile targetPcID];
      ```

* **targetSessionID**

   Retorna o SessionID.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSString *myTargetSessionID = [ADBMobile targetSessionID];
      ```

### Exemplo

```objective-c
// make your request 
ADBTargetLocationRequest *myRequest =  
 [ADBMobile targetCreateRequestWithName:@"heroBanner"  
                         defaultContent:@"default.png"  
                          parameters:nil]; 
// load your request 
[ADBMobile targetLoadRequest:myRequest  
                    callback:^(NSString *content) { 
                        // do something with content 
                        heroImage.image = [UIImage imageNamed:content];
                    }];
```
