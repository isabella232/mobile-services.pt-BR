---
description: Esta é uma lista de métodos do Adobe Analytics fornecidos pela biblioteca do iOS.
seo-description: Esta é uma lista de métodos do Adobe Analytics fornecidos pela biblioteca do iOS.
seo-title: Métodos do Analytics
solution: Marketing Cloud,Analytics
title: Analytics methods
topic: Desenvolvedor e implementação
uuid: d49fe6de-cb32-4b96-9891-c567310e59a6
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Analytics methods {#analytics-methods}

Esta é uma lista de métodos do Adobe Analytics fornecidos pela biblioteca do iOS.

O SDK suporta atualmente várias Soluções da Adobe Experience Cloud, incluindo o Analytics, o Target, o Audience Manager e o Adobe Experience Platform Identity Service. Methods are prefixed according to the solution. Experience Cloud ID methods are prefixed with `track`.

Cada um desses métodos é usado para enviar dados para seu conjunto de relatórios do Adobe Analytics.

* **trackState:&#x200B;data:**

   States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. Esses estados são semelhantes às páginas em um site e as chamadas de `trackState` aumentam as exibições de página. If `state` is empty, it displays as *app name app version (build)* in reports. If you see this value in reports, ensure you are setting `state` in each `trackState` call.

   >[!TIP]
   >
   >This is the only tracking call that increments page views.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ````

* **trackAction:&#x200B;data:**

   Rastreia uma ação no seu aplicativo. Actions that you want to measure, such as `logons`, `banner taps`, `feed subscriptions`, and other metrics, occur in your app.

   >[!TIP]
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

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
   >This method should only be called in code that runs while your app is in the background.

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

   Transmite `data` para atualizar os dados de contexto associados à `action`. The `data` that is passed in is appended to the existing data for the action, and if the same key is already defined for `action`, overwrites the data.

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

   Encerra uma ação programada. If you provide `block`, you will have access to the final time values and be able to manipulate `data` prior to sending the final hit.

   >[!TIP]
   >
   >If you provide `block`, you must return `YES` to send a hit. Passing in `nil` for `block` sends the final hit.

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

   Requires SDK 4.1. Regardless of how many hits are currently queued, forces the library to send all hits in the offline queue.

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
   >This method does not increment page views.

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
