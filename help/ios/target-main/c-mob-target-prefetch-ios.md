---
description: O recurso de busca prévia do Adobe Target usa o SDK móvel do iOS para buscar conteúdos em oferta a menor quantidade de vezes possível ao armazenar as respostas do servidor em cache.
title: Realizar uma busca prévia por conteúdos em oferta no iOS
uuid: fef58042-65e2-4579-b8f1-d21554d2af57
exl-id: 64d43be7-6bd1-4657-8154-5b2c1cbbf42b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 85%

---

# Realizar uma busca prévia por conteúdos em oferta no iOS {#prefetch-offer-content-in-ios}

O recurso de busca prévia do Adobe Target usa o SDK móvel do iOS para buscar conteúdos em oferta a menor quantidade de vezes possível ao armazenar as respostas do servidor em cache.

>[!IMPORTANT]
>
>A funcionalidade de busca prévia nos SDKs móveis para iOS não é compatível com os tipos de atividades de Destino automático, Alocação automática e Personalização automatizada no Adobe Target.

Esse processo reduz o tempo de carregamento, previne várias chamadas de rede e permite que o Adobe Target seja notificado sobre qual mbox foi visitada pelo usuário do aplicativo móvel. Todo o conteúdo será recuperado e armazenado em cache durante a chamada da busca prévia, e esse conteúdo será recuperado do cache para todas as chamadas futuras que contenham conteúdo armazenado em cache para o nome da mbox especificado.

O conteúdo da busca prévia não persiste entre inicializações. O conteúdo da busca prévia é armazenado em cache enquanto o aplicativo estiver executando ou até que o método `clearPrefetchCache()` seja chamado.

>[!IMPORTANT]
>
>As APIs de busca prévia do Target estão disponíveis desde a versão 4.14.0 do SDK. Para obter mais informações sobre as limitações de parâmetros, consulte [Parâmetros de entrada de lotes](https://developers.adobetarget.com/api/#batch-input-parameters).

No SDK de versão 4.14 ou posterior, se especificado, a `environmentId``ADBMobileConfig.json` é extraída do arquivo ao iniciar uma chamada v2 batch mbox TnT. Caso nenhuma `environmentId` esteja especificada nesse arquivo, nenhum parâmetro de ambiente é enviado pela chamada TNT batch mbox, e a oferta é entregue ao ambiente padrão.

Por exemplo:

```
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Métodos de busca prévia {#section_05967F1F3A554B0FBC2C08A954554BDE}

Estes são os métodos que podem ser usados para realizar a busca prévia no iOS:

* **targetPrefetchContent**

   Envia uma solicitação de busca prévia com uma matriz de localizações para o servidor do Target configurado e retorna o status da solicitação na chamada de retorno fornecida.

   * Esta é a sintaxe para este método:

      ```objective-c
      (void) targetPrefetchContent:(nonnull NSArray*)targetPrefetchObjectArray 
                     withProfileParameters:(nullable NSDictionary*)profileParameters 
                            callback:(nullable void(^)(BOOL success))callback;
      ```

   * Estes são os parâmetros para este método:

      * **`targetPrefetchArray`**

         Matriz de `TargetPrefetchObjects` que contém o nome e os mboxParameters para cada localização do Target na qual se deve realizar uma busca prévia.

      * **`profileParameters`**

         Contém as chaves e os valores dos parâmetros de perfil a ser usados com cada localização de busca prévia nesta solicitação.

      * **`callback`**

         Invocado quando a busca prévia está concluída. Retorna `true` se a busca prévia foi bem-sucedida, e `false` caso contrário.

* **targetLoadRequests**

   Executa uma solicitação em lote em várias localizações de mbox especificadas no vetor de solicitações. Cada objeto na matriz contém uma função de chamada de retorno, que será invocada quando o conteúdo estiver disponível na localização da mbox fornecida.

   >[!IMPORTANT]
   >
   >Se o conteúdo das localizações solicitadas já estiver armazenado em cache, ele será retornado imediatamente na chamada de retorno fornecida. Caso contrário, o SDK enviará uma solicitação de rede para que os servidores do Target recuperem o conteúdo.

   * Esta é a sintaxe para este método:

      ```objective-c
      (void)targetLoadRequests:(nonnullNSArray*)requests 
               withProfileParameters:(nullableNSDictionary*)profileParameters;
      ```

   * Estes são os parâmetros para este método:

      * **`requests`**

         Matriz de `TargetRequestObjects` que contém o nome, o conteúdo padrão, os parâmetros e a função de chamada de retorno para cada localização a ser recuperada.

      * **`profileParameters`**

         Contém as chaves e os valores dos parâmetros de perfil a ser usados com cada localização de busca prévia nesta solicitação.

* **targetPrefetchClearCache**

   Limpa os dados armazenados em cache pela busca prévia do Target.

   * Esta é a sintaxe para este método:

      ```objective-c
      (void) targetPrefetchClearCache; 
      ```

   * Não há parâmetros para este método.

* **targetRequestObjectWithName**

   Cria e retorna uma instância de `TargetRequestObject` com os dados fornecidos.

   * Esta é a sintaxe para este método:

      ```objective-c
      +(nullableADBTargetRequestObject*)targetRequestObjectWithName:(nonnullNSString*)name
      defaultContent:(nonnullNSString*)defaultContent
      mboxParameters:(nullableNSDictionary*)mboxParameters
      callback:(nullablevoid(^)(NSString*__nullablecontent))callback;
      ```

   * Não há parâmetros para este método.

* **createTargetPrefetchObject**

   Cria e retorna uma instância de `TargetPrefetchObject` com os dados fornecidos.

   * Esta é a sintaxe para este método:

      ```objective-c
      +(nullable ADBTargetPrefetchObject *) targetPrefetchObjectWithName:(nonnullNSString *)name
      mboxParameters:(nullableNSDictionary *)mboxParameters;
      ```

## Classes públicas {#section_A273E53F069E4327BBC8CE4910B37888}

Estas são as classes públicas que oferecem suporte para a busca prévia no iOS:

### Referência da classe: TargetPreFetchObject

Encapsula o nome e os parâmetros da mbox usados na busca prévia da mbox.

* **`name`**

   Nome do local/mbox que você deseja recuperar.

   * **Tipo**: NSString*

* **`mboxParameters`**

   Um dicionário opcional que contém os pares de chave-valor para os parâmetros da mbox.

   * **Tipo**: NSDictionary*

* **`orderParameters`**

   Dicionário que contém os pares de chave-valor para os parâmetros de ordem.

   * **Tipo**: NSDictionary*

* **`productParameters`**

   Dicionário que contém os pares de chave-valor para os parâmetros de produto.

   * **Tipo**: NSDictionary*

### Referência de classe: TargetRequestObject

Essa classe encapsula o nome da mbox, o conteúdo padrão, os parâmetros da mbox e a função de retorno usada nas solicitações de localização do Target.

* **`name`**

   Nome da localização solicitada.

   * **Tipo**: NSString*

* **`mboxParameters`**

   O valor NSString que representa o nome do local/mbox que você deseja recuperar.

   * **Tipo**: NSString*

* **`defaultContent`**

   O conteúdo padrão que será retornado se os servidores do Target não puderem ser acessados.

   * **Tipo**: NSString*

* **`callback`**

   Quando o lote solicita as localizações do Target, a chamada de retorno será invocada quando o conteúdo estiver disponível nesta localização.

   * **Tipo**: função

## Amostra de código {#section_BF7F49763D254371B4656E17953D520C}

Este é um exemplo de como realizar uma busca prévia por conteúdo por meio dos SDKs do iOS:

```objective-c
/** 
 * Prefetch Content 
 */ 
  
    NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
    NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
    NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
  
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    // Creating Prefetch Objects 
    ADBTargetPrefetchObject *prefetch1 = [ADBMobile targetPrefetchObjectWithName:@"logo" mboxParameters:mboxParameters1]; 
    prefetch1.productParameters = productParameters1; 
    prefetch1.orderParameters = orderParameters1; 
  
    ADBTargetPrefetchObject *prefetch2 = [ADBMobile targetPrefetchObjectWithName:@"buttonColor" mboxParameters:mboxParameters2]; 
    prefetch2.productParameters = productParameters2; 
    prefetch2.orderParameters = orderParameters2; 

    // Creating prefetch Array 
    NSArray *prefetchArray = @[prefetch1,prefetch2]; 
  
    // Creating Profile parameters 
    NSDictionary *profileParmeters = @{@"age":@"20-32"};

    // Target API Call 
    [ADBMobile targetPrefetchContent:prefetchArray withProfileParameters:profileParmeters callback:^(BOOL isSuccess){ 
       // do something with the Boolean result 
    }];
```

Este é um exemplo de `loadRequest` em lote com os SDKs do iOS:

```objective-c
/** 
 * Batch loadRequest  
 */ 
  
   NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
   NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
   NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    ADBTargetRequestObject *request1 = [ADBMobile targetRequestObjectWithName:@"logo" defaultContent:@"BlueWhale" mboxParameters:mboxParameters1 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
  
    request1.productParameters = productParameters1; 
    request1.orderParameters = orderParameters1;

    ADBTargetRequestObject *request2 = [ADBMobile targetRequestObjectWithName:@"buttonColor" defaultContent:@"red" mboxParameters:mboxParameters2 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
    request2.productParameters = productParameters1; 
    request2.orderParameters = orderParameters1;

    // create request object array 
    NSArray *requestArray = @[request1,request2]; 
  
    // Call the API 
    [ADBMobile targetLoadRequests:requestArray withProfileParameters:profileParmeters];
```

## Informações adicionais {#section_A454BAD1CD49423E86C71BAEE06125FD}

Estas são algumas informações adicionais sobre essas amostras:

* `ProductParameters` permite somente as seguintes chaves:

   * `id`
   * `categoryId`

* `OrderParameters` permite somente as seguintes chaves:

   * `id`
   * `total`
   * `purchasedProductIds`

* `purchasedProducts` aceita uma matriz de sequências de caracteres.
