---
description: Esta é uma lista de métodos do Adobe Analytics fornecida pela biblioteca do Android.
keywords: android;library;mobile;sdk
seo-description: Esta é uma lista de métodos do Adobe Analytics fornecida pela biblioteca do Android.
seo-title: Métodos do Analytics
solution: Marketing Cloud,Analytics
title: Métodos do Analytics
topic: Developer and implementation
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
translation-type: ht
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: ht
source-wordcount: '740'
ht-degree: 100%

---


# Métodos do Analytics {#analytics-methods}

Esta é uma lista de métodos do Adobe Analytics fornecida pela biblioteca do Android.

Atualmente, o SDK é compatível com várias soluções da Adobe Experience Cloud, como o Analytics, o Target, o Audience Manager e o Adobe Experience Platform Identity Service. Os métodos recebem o prefixo de acordo com a solução, por exemplo, métodos da Experience Cloud ID recebem o prefixo `analytics`.

Cada um destes métodos é usado para enviar dados para o conjunto de relatórios do Adobe Analytics:

* **trackState**

   Rastreia um estado de aplicativo com dados de contexto opcionais. Os estados são as exibições disponíveis no aplicativo, como `home dashboard`, `app settings`, `cart`, e assim por diante. Esses estados são semelhantes às páginas em um site, e as chamadas de `trackState` aumentam as visualizações de página.

   Se `state` estiver vazio, `app name app version (build)` será exibido nos relatórios. Caso veja esse valor em relatórios, certifique-se de configurar `state` em cada chamada de `trackState`.

   >[!TIP]
   >
   >Esta é a única chamada de rastreamento que aumenta as exibições de página.

   * Esta é a sintaxe para este método:

      ```java
      public static void trackState(String state, Map<String, Object> contextData);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.trackState("loginScreen", null);
      ```

* **trackAction**
Rastreia uma ação no seu aplicativo.

   Ações que deseja medir, como `logons`, `banner taps`, `feed subscriptions` e outras métricas que ocorrem no aplicativo.

   * Esta é a sintaxe para este método:

      ```java
      public static void trackAction(String state, Map<String, Object> contextData);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.trackAction("heroBannerTouched", null);
      ```

* **getTrackingIdentifier**
Retorna o identificador de visitante gerado automaticamente pelo Analytics.

   Esta é uma ID de visitante exclusiva e específica do aplicativo, gerada na primeira inicialização e armazenada e usada a partir desse ponto. A ID é preservada entre as atualizações do aplicativo e é removida quando o aplicativo é desinstalado.

   * Esta é a sintaxe para este método:

      ```java
      public static String getTrackingIdentifier();
      ```

   * Esta é a amostra de código para este método:

      ```java
      String trackingId = Analytics.getTrackingIdentifier();
      ```

* **trackLocation**

   Envia latitude, longitude e localização atuais em um ponto de interesse definido. Para obter mais informações, consulte [Geolocalização e pontos de interesse](/help/android/location/geo-poi.md).

   * Esta é a sintaxe para este método:

      ```java
      public static void trackLocation(Location location, Map<String, Object> contextData);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.trackLocation(userLocation, null);
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Adiciona uma `amount` ao valor do ciclo de vida do usuário.

   * Esta é a sintaxe para este método:

      ```java
      public static void trackLifetimeValueIncrease(BigDecimal amount, Map<String, Object> contextData);
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
   public static void trackTimedActionStart(String action, Map<String, Object> contextData);
   ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.trackTimedActionStart("cartToCheckout", null)
      ```


* **trackTimed&#x200B;ActionUpdate**

   Passa em `contextData` para atualizar os dados de contexto associados a `action`. Os `data` passados estão anexados aos dados existentes da ação e, se a mesma chave já estiver definida como `action`, eles substituirão os dados.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```java
      public static void trackTimedActionUpdate(String action, Map<String, Object> contextData);
      ```

   * Esta é uma amostra de código para este método:

      ```java
      HashMap cdata = new HashMap<String Object> ();
      cdata.put("quantity",3);
      Analytics.trackTimedActionUpdate("cartToCheckout", cdata);
      ```

* **trackTimed&#x200B;ActionEnd**

   Encerra uma ação programada. Se você fornecer `block`, poderá acessar os valores de tempo finais e manipular `data` antes de enviar a ocorrência final.

   >[!TIP]
   >
   >Se você fornecer `block`, deverá retornar `true` para enviar uma ocorrência. Passar `null` para `block` envia a ocorrência final.

   * Esta é a sintaxe para este método:

      ```java
      public static void trackTimedActionEnd(String action, TimedActionBlock<Boolean> logic);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.trackTimedActionEnd("cartToCheckout",new
      Analytics.TimedActionBlock<Boolean>(){
          @Override
          public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) {
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
      public static void sendQueuedHits();
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.sendQueuedHits();
      ```

* **getQueueSize**

   Devolve o número de chamadas de rastreamento armazenadas na fila offline.

   * Esta é a sintaxe para este método:

      ```java
      public static long getQueueSize();
      ```

   * Esta é a amostra de código para este método:

      ```java
      long queueSize = Analytics.getQueueSize();
      ```

* **clearQueue**

   Apaga todas as ocorrências da fila offline.

   * Esta é a sintaxe para este método:

      ```java
      public static void clearQueue();
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.clearQueue();
      ```

      >[!WARNING]
      >
      > Tenha cuidado ao limpar manualmente a fila. Esse processo não pode ser revertido.

* **processReferrer**

   Processa dados de campanha do referenciador da Google Play Store para uso posterior.

   * Esta é a sintaxe para este método:

      ```java
      public static void processReferrer(final Context context, final Intent intent);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.processReferrer(getApplicationContext(), intent);
      ```

* **processGooglePlayInstallReferrerUrl**

   >[!IMPORTANT]
   >
   > Essa API está disponível a partir do SDK versão 4.18.0

   Recupera dados de aquisição do URL do Referenciador de instalação do Google Play fornecido.

   Os dados coletados dessa API serão enviados com ocorrências de instalação enviadas ao Analytics e estarão disponíveis na chamada de retorno de dados da Adobe.

   Se os dados do referenciador já tiverem sido coletados pelo SDK, chamar esse método resultará em uma operação inútil.

   Para obter informações sobre como recuperar o URL do referenciador, consulte a documentação do Google: https://developer.android.com/google/play/installreferrer/library.

   * Esta é a sintaxe para este método:

      ```java
      public static void processGooglePlayInstallReferrerUrl(final String referrerUrl);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);
      ```
