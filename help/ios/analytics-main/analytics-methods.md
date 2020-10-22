---
description: Esta é uma lista de métodos do Adobe Analytics fornecidos pela biblioteca do iOS.
seo-description: Esta é uma lista de métodos do Adobe Analytics fornecidos pela biblioteca do iOS.
seo-title: Métodos do Analytics
solution: Experience Cloud,Analytics
title: Métodos do Analytics
topic: Developer and implementation
uuid: d49fe6de-cb32-4b96-9891-c567310e59a6
translation-type: ht
source-git-commit: bc11c1e7a4a11657ee89c40ddcbd37377ce50bb5
workflow-type: ht
source-wordcount: '784'
ht-degree: 100%

---


# Métodos do Analytics {#analytics-methods}

Esta é uma lista de métodos do Adobe Analytics fornecidos pela biblioteca do iOS.

Atualmente, o SDK é compatível com várias soluções da Adobe Experience Cloud, como o Analytics, o Target, o Audience Manager e o Adobe Experience Platform Identity Service. Métodos recebem o prefixo de acordo com a solução. Os métodos da Experience Cloud ID recebem o prefixo `track`.

Cada um desses métodos é usado para enviar dados para seu conjunto de relatórios do Adobe Analytics.

* **trackState:&#x200B;data:**

   Os estados são as exibições disponíveis no aplicativo, como `home dashboard`, `app settings`, `cart`, e assim por diante. Esses estados são semelhantes às páginas em um site, e as chamadas de `trackState` aumentam as visualizações de página. Se `state` estiver vazio, ele é exibido como *nome do aplicativo versão do aplicativo (build)* nos relatórios. Caso veja esse valor em relatórios, certifique-se de configurar um `state` em cada chamada de `trackState`.

   >[!TIP]
   >
   >Esta é a única chamada de rastreamento que aumenta as exibições de página.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ```

* **trackAction:&#x200B;data:**

   Rastreia uma ação no seu aplicativo. Ações que deseja medir, como `logons`, `banner taps`, `feed subscriptions` e outras métricas, ocorrem no aplicativo.

   >[!TIP]
   >
   >Se você tem um código que pode funcionar enquanto o aplicativo é executado em segundo plano (por exemplo, uma recuperação de dados em segundo plano), use `trackActionFromBackground`.

   * Esta é a sintaxe para este método:

      ```objective-c
      +  (void)  trackAction:(NSString  *)action
                        data:(NSDictionary  *)data; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile  trackAction:@"heroBannerTouched"
                         data:nil]; 
      ```

* **trackingIdentifier**

   Recupera o identificador do rastreamento de análises.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (NSString *) trackingIdentifier; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSString *trackingId = [ADBMobile trackingIdentifier];
      ```

* **trackActionFromBackground:&#x200B;data:**

   Rastreia uma ação que ocorreu em segundo plano, o que impede os eventos do ciclo de vida de dispararem em determinados cenários.

   >[!TIP]
   >
   >Este método deve ser chamado somente no código em execução enquanto o aplicativo estiver em segundo plano.

   * Esta é a sintaxe para este método:

      ```objective-c
       +  (void)  trackActionFromBackground:(NSString  *)action
                                       data:(NSDictionary  *)data; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile  trackActionFromBackground:@"downloadedUpdate"
                                       data:nil];
      ```

* **trackLocation:&#x200B;data:**

   Envia as coordenadas x e y atuais. Também usa pontos de interesse definidos no arquivo `ADBMobileConfig.json` a fim de determinar se o local fornecido como parâmetro está no POI. Se as coordenadas atuais estão dentro de um POI definido, uma variável de dados de contexto é preenchida e enviada com a chamada `trackLocation`.

   * Esta é a sintaxe para este método:

      ```objective-c
      +  (void)  trackLocation:(CLLocation  *)location
                          data:(NSDictionary  *)data; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile  trackLocation:userLocation
                           data:nil]; 
      ```

* **trackBeacon:&#x200B;data:**

   Rastreia quando um usuário está perto de um beacon.

   * Esta é a sintaxe para este método:

      ```objective-c
      +  (void)  trackLocation:(CLBeacon  *)beacon
                          data:(NSDictionary  *)data;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile  trackBeacon:beacon
                         data:nil];
      ```

* **trackingClearCurrentBeacon**

   Apaga os dados de beacons depois que o usuário se distancia de um.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) trackingClearCurrentBeacon;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile trackingClearCurrentBeacon];
      ```

* **trackLifetimeValueIncrease:&#x200B;data:**

   Adiciona uma `amount` ao valor do ciclo de vida do usuário.

   * Esta é a sintaxe para este método:

      ```objective-c
       +  (void)  trackLifetimeValueIncrease:(NSDecimalNumber  *)amount
                                       data:(NSDictionary  *)data; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile  trackLifetimeValueIncrease:30
                                         data:nil];
      ```

* **trackTimedActionStart:&#x200B;data:**

   Inicia uma ação programada com a `action` de nome. Se você chamar este método para uma ação já iniciada, a ação programada anterior será substituída.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```objective-c
      +  (void)  trackTimedActionStart:(NSString  *)action
                                  data:(NSDictionary  *)data; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile  trackTimedActionStart:@"cartToCheckout"
                                  data:nil]; 
      ```

* **trackTimedActionUpdate:&#x200B;data:**

   Transmite `data` para atualizar os dados de contexto associados à `action`. Os `data` passados estão anexados aos dados existentes da ação e, se a mesma chave já estiver definida como `action`, eles substituirão os dados.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```objective-c
       +  (void)  trackTimedActionUpdate:(NSString  *)action
                                    data:(NSDictionary  *)data; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile  trackTimedActionUpdate:@"cartToCheckout"
                                    data:@{@"quantity":@"3"}];
      ```

* **trackTimedActionEnd:&#x200B;logic:**

   Encerra uma ação programada. Se você fornecer `block`, terá acesso aos valores de tempo finais e poderá manipular os `data` antes de enviar a ocorrência final.

   >[!TIP]
   >
   >Se você fornecer `block`, deverá retornar `YES` para enviar uma ocorrência. Transmitir `nil` para `block` envia a ocorrência final.

   * Esta é a sintaxe para este método:

      ```objective-c
      +  (void)  trackTimedActionEnd:(NSString  *)action
                          logic:(BOOL  (^)  (NSTimeInterval  inAppDuration,
                                                  NSTimeInterval totalDuration,
                                                  NSMutableDictionary *data))block; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile  trackTimedActionEnd:@"cartToCheckout"
                    logic:^(NSTimeInterval inApp,
                    NSTimeInterval  total,
                    NSMutableDictionary  *data)  {
                        data[@"price"]  =  @"49.95";
                        return  YES;
                    }];
      ```

* **trackingTimedActionExists**

   Retorna se uma ação cronometrada estiver em andamento.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (BOOL) trackingTimedActionExists:(NSString *)action;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      BOOL *actionExists = [ADBMobile trackingTimedActionExists];
      ```

* **trackingSendQueuedHits**

   Exige SDK 4.1. Independentemente da quantidade de ocorrências presentes atualmente na fila, força a biblioteca a enviar todas as ocorrências da fila offline.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) trackingSendQueuedHits;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile trackingSendQueuedHits]; 
      ```

* **trackingGetQueueSize**

   Recupera o número de ocorrências na fila offline.

   * Esta é a sintaxe para este método:

      ```objective-c
       + (NSUInteger) trackingGetQueueSize;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSUInteger *queueSize = [ADBMobile trackingGetQueueSize];
      ```

* **trackingClearQueue**

   Apaga todas as ocorrências da fila offline.

   >[!CAUTION]
   >
   >Tenha cuidado ao limpar a fila manualmente. Esse processo não pode ser revertido.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) trackingClearQueue;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile trackingClearQueue]; 
      ```



* **trackPushMessageClickThrough**

   Rastreia um clique na mensagem por push.

   >[!IMPORTANT]
   >
   >Este método não incrementa as visualizações de página.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) trackPushMessageClickThrough:(NSDictionary *)userInfo;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      -  (void)application:(UIApplication  *)application  
      didReceiveRemoteNotification:(NSDictionary  *)userInfo  
      fetchCompletionHandler:(void  (^)
      (UIBackgroundFetchResult))completionHandler  {
          // only send the hit if the app is not active
          if (application.applicationState !=  UIApplicationStateActive)  {
              [ADBMobile  trackPushMessageClickThrough:userInfo];
      
          }
          completionHandler(UIBackgroundFetchResultNoData);
      }
      ```
