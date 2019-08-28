---
description: Esta é uma lista de métodos do Adobe Target fornecidos pela biblioteca do iOS.
seo-description: Esta é uma lista de métodos do Adobe Target fornecidos pela biblioteca do iOS.
seo-title: Métodos do iOS para o Adobe Mobile Services
solution: Marketing Cloud, Analytics
title: Métodos de meta para iOS
topic: Desenvolvedor e implementação
uuid: 692 bcda 1-02 ba -4902-bd 65-15888 adf 1952
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Métodos do Target para iOS {#target-methods}

Esta é uma lista de métodos do Adobe Target fornecidos pela biblioteca do iOS.

O SDK atualmente tem suporte para várias Soluções da Adobe Experience Cloud, incluindo Analytics, Target, Audience Manager e Adobe Experience Platform Identity Service. Os métodos apresentam prefixos de acordo com a solução. Por exemplo, os métodos do têm o prefixo `target`target.

>[!TIP]
>
>Medições de ciclo de vida são enviadas como parâmetros para cada carregamento de mbox. Para obter mais informações, consulte [Medições de ciclo de vida](/help/ios/metrics.md).

## Referência de classe: Adbtargetlocationrequest

### Propriedades

```objective-c
NSString *name; 
NSString *defaultContent; 
NSMutableDictionary *parameters;
```

### Constantes da string

>[!TIP]
>
>As constantes a seguir são para facilitar o uso quando você define chaves para parâmetros personalizados.

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
>* If you are using SDKs **before** version 4.14.0, see [Input Parameters](https://developers.adobetarget.com/api/#input-parameters) for parameters limitations.
   >
   >
* If you are using SDKs version 4.14.0 **or after**, see [Batch Input Parameters](https://developers.adobetarget.com/api/#batch-input-parameters) for parameters limitations.


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

* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:requestLocationParameters:callback:**

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

         Os valores neste dicionário serão adicionados ao objeto "profileParameters" na solicitação para o Target.

         * **Tipo**: NSDictionary*
      * **`orderParameters`**

         Os valores neste dicionário serão adicionados ao objeto "order" na solicitação para o Target.

         * **Tipo**: NSDictionary
      * **`mboxParameters`**

         Os valores neste dicionário serão adicionados ao objeto "mboxParameters" na solicitação para o Target.

         * **Tipo**: NSDictionary*
      * **`requestLocationParameters`**

         Os valores neste dicionário serão adicionados ao objeto "requestLocation" na solicitação para o Target.

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

      Para obter mais informações sobre a API subjacente do Target, consulte [Desenvolvedores do Adobe Target](https://docs.adobe.com/dev/products/target/reference/delivery.html).







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
