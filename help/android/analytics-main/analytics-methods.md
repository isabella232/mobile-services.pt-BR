---
description: Esta é uma lista de métodos do Adobe Analytics fornecida pela biblioteca do Android.
keywords: android;biblioteca;móvel;sdk
seo-description: Esta é uma lista de métodos do Adobe Analytics fornecida pela biblioteca do Android.
seo-title: Métodos do Analytics
solution: Marketing Cloud,Analytics
title: Métodos do Analytics
topic: Desenvolvedor e implementação
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

Esta é uma lista de métodos do Adobe Analytics fornecida pela biblioteca do Android.

The SDK currently supports multiple Adobe Experience Cloud Solutions], including Analytics], Target], Audience Manager], and the Adobe Experience Platform Identity Service]. Os métodos recebem o prefixo de acordo com a solução, por exemplo, métodos da Experience Cloud ID recebem o prefixo `analytics`.

Cada um destes métodos é usado para enviar dados para o conjunto de relatórios do Adobe Analytics:

* **trackState**

   Rastreia um estado de aplicativo com dados de contexto opcionais. States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. Esses estados são semelhantes às páginas em um site e as chamadas de `trackState` aumentam as exibições de página.

   If `state` is empty, `app name app version (build)` is displayed in reports. Caso veja esse valor em relatórios, certifique-se de configurar `state` em cada chamada de `trackState`.

   >[!TIP]
   >
   >Essa é a única chamada de rastreamento que aumenta as exibições de página.

   * Esta é a sintaxe para este método:

      ```java
      public staticvoidtrackState(Stringstate, Map<String,Object> contextData);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.trackState("loginScreen",null);
      ```

* **trackAction** Rastreia uma ação no aplicativo.

   Actions that you want to measure, such as `logons`, `banner taps`, `feed subscriptions`, and other metrics, that occur in your app.

   * Esta é a sintaxe para este método:

      ```java
      publicstaticvoidtrackAction(Stringstate,Map<String,Object> contextData);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.trackAction("heroBannerTouched",null);
      ```

* **getTrackingIdentifier** Retorna o identificador de visitante gerado automaticamente para o Analytics.

   Esta é uma ID de visitante única e específica do aplicativo gerada na primeira inicialização, armazenada e utilizada a partir desse ponto. A ID é preservada entre as atualizações do aplicativo e é removida quando o aplicativo é desinstalado.

   * Esta é a sintaxe para este método:

      ```java
      public static String getTrackingIdentifier(); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      String trackingId = Analytics.getTrackingIdentifier(); 
      ```

* **trackLocation**

   Envia a latitude, a longitude e o local atuais em um ponto de interesse definido. Para obter mais informações, consulte [Localização geográfica e pontos de interesse](/help/android/location/geo-poi.md).

   * Esta é a sintaxe para este método:

      ```java
      public static void trackLocation(Location location, Map<String,Object> contextData); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.trackLocation(userLocation, null);
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Adiciona uma `amount` ao valor do ciclo de vida do usuário.

   * Esta é a sintaxe para este método:

      ```java
      publicstaticvoidtrackLifetimeValueIncrease(BigDecimalamount,Map<String,Object>contextData);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.trackLifetimeValueIncrease(new BigDecimal(30), null);
      ```

* **trackTimed&#x200B;ActionStart**

   Inicia uma ação programada com a `action` de nome.

   Se você chamar este método para uma ação já iniciada, a ação programada anterior será substituída.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:
   ```java
   publicstaticvoidtrackTimedActionStart(Stringaction,Map<String,Object>contextData);
   ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.trackTimedActionStart("cartToCheckout",null)
      ```


* **trackTimed&#x200B;ActionUpdate**

   Pass in `contextData` to update the context data that is associated with the `action`. The `data` that is passed in is appended to the existing data for the action, and if the same key is already defined for `action`, overwrites the data.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```java
      public static void trackTimedActionUpdate(Stringaction,Map <String,Object> contextData); 
      ```

   * Esta é uma amostra de código para este método:

      ```java
      HashMap cdata = new HashMap<String Object> (); 
      cdata.put("quantity",3); 
      Analytics.trackTimedActionUpdate("cartToCheckout", cdata);
      ```

* **trackTimed&#x200B;ActionEnd**

   Encerra uma ação programada. If you provide `block`, you can access the final time values and can manipulate `data` before sending the final hit.

   >[!TIP]
   >
   >If you provide `block`, you must return `true` to send a hit. Passing `null` for `block` sends the final hit.

   * Esta é a sintaxe para este método:

      ```java
      public static void trackTimedActionEnd(Stringaction,TimedActionBlock<Boolean> logic); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.trackTimedActionEnd("cartToCheckout",new
      Analytics.TimedActionBlock<Boolean>(){
        @Override
        public Booleancall(long inAppDuration,long totalDuration, Map<String,
      Object> contextData) {
              contextData.put("price", 49.95);
              return true;
         }
      });
      ```

* **sendQueuedHits**

   **Exige SDK 4.1.**

   Independentemente de quantas ocorrências estejam na fila, esse método faz com que biblioteca envie todas as ocorrências para a fila offline.

   * Esta é a sintaxe para este método:

      ```java
      voidsendQueuedHits()
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.sendQueuedHits();
      ```

* **getQueueSize**

   Devolve o número de chamadas de rastreamento armazenadas na fila offline.

   * Esta é a sintaxe para este método:

      ```java
      long getQueueSize()
      ```

   * Esta é a amostra de código para este método:

      ```java
      long queueSize = Analytics.getQueueSize(); 
      ```

* **clearQueue**

   Apaga todas as ocorrências da fila offline.

   * Esta é a sintaxe para este método:

      ```java
      voidclearQueue()
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.clearQueue();
      ```

      >[!WARNING]
      >
      > Tenha cuidado ao limpar manualmente a fila. Esse processo não pode ser revertido.