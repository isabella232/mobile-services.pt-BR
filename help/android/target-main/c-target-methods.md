---
description: Esta é a lista de métodos do Adobe Target fornecida pela biblioteca do Android.
keywords: android;biblioteca;móvel;sdk
solution: Experience Cloud,Analytics
title: Métodos do Target para o Android
topic-fix: Developer and implementation
uuid: 8e9808b2-ba80-4646-ba05-8e62d4fde065
exl-id: 0c7a6718-d078-4a2b-a2c9-d5cd50263939
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 95%

---

# Métodos do Target para o Android{#target-methods}

Esta é a lista de métodos do Adobe Target fornecida pela biblioteca do Android.

Atualmente, o SDK é compatível com várias soluções da Adobe Experience Cloud, como o Analytics, o Target, o Audience Manager e o Adobe Experience Platform Identity Service. Os métodos recebem o prefixo de acordo com a solução. Por exemplo, métodos da Experience Cloud ID recebem o prefixo `target`.

>[!TIP]
>
>[Medições de ciclo de vida](/help/android/metrics.md) são enviadas como parâmetros para cada carregamento de mbox.

## Referência de classe: TargetLocationRequest {#section_A8CC898922164E819EC730DC92A6742B}

**Propriedades:**

```java
public String name; 
public String defaultContent; 
public HashMap<String, Object> parameters;
```

**Constantes da cadeia de caracteres**

>[!TIP]
>
>As constantes seguintes facilitam o uso ao configurar as chaves para parâmetros personalizados.

```java
public static final String TARGET_PARAMETER_ORDER_ID   = "orderId"; 
public static final String TARGET_PARAMETER_ORDER_TOTAL         = "orderTotal"; 
public static final String TARGET_PARAMETER_PRODUCT_PURCHASE_ID = "productPurchasedId"; 
public static final String TARGET_PARAMETER_CATEGORY_ID         = "categoryId"; 
public static final String TARGET_PARAMETER_MBOX_3RDPARTY_ID    = "mbox3rdPartyId"; 
public static final String TARGET_PARAMETER_MBOX_PAGE_VALUE     = "mboxPageValue"; 
public static final String TARGET_PARAMETER_MBOX_PC             = "mboxPC"; // pcId in cookie 
public static final String TARGET_PARAMETER_MBOX_SESSION_ID     = "mboxSession"; // sessionId in cookie 
public static final String TARGET_PARAMETER_MBOX_HOST           = "mboxHost";
```

>[!IMPORTANT]
>
>* Se você estiver usando SDKs **anteriores** à versão 4.14.0, consulte [https://developers.adobetarget.com/api/#input-parameters](https://developers.adobetarget.com/api/#input-parameters) para limitações de parâmetros.
>
>* Se você estiver usando SDKs versão 4.14.0 **ou posterior**, consulte [https://developers.adobetarget.com/api/#batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters) para limitações de parâmetros.


* **loadRequest**

   Envia request para o servidor do Target configurado e retorna o valor da cadeia de caracteres da oferta gerada em um callback de bloqueio.

   * Esta é a sintaxe para este método:

      ```java
      public static void loadRequest(TargetLocationRequest request, TargetCallback<String> callback);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Target.loadRequest(heroBannerRequest, new Target.TargetCallback<String>() {  @Override  public void call(String item) {   // do something with item  } });
      ```

* **loadRequest**

   Envia request para o servidor do Target configurado e retorna o valor da cadeia de caracteres da oferta gerada em um callback de bloqueio.

   * Esta é a sintaxe para este método:

      ```java
      public static void loadRequest(final String name final String defaultContent, final Map `<String, Object>` profileParameters, 
                                     final Map `<String, Object>` orderParameters,final Map `<String Object>` mboxParameters, final TargetCallback<String> callback)
      ```

   * Esta é a amostra de código para este método:

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put("profile-parameter-key", "profile-parameter-value"); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put("order-parameter-key", "order-parameter-value");
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); 
      mboxParameters.put("mbox-parameter-key", "mbox-parameter-value"); 
      Target.loadRequest("mboxName", "defaultContent", profileParameters, orderParameters, mboxParameters
      new TargetCallback<String>() {
          @Override
          public void call (String item) {
             Log.d("Target Content", item); 
          }
      });
      ```

* **loadRequest**

   Envia uma solicitação para o servidor do Target configurado e retorna o valor da sequência de caracteres da oferta gerada em um TargetCallback.

   * Esta é a sintaxe para este método:

      ```java
      public static void loadRequest(final String name, final String defaultContent, final Map<String, Object> profileParameters, final Map<String, Object> orderParameters, final Map<String, Object> mboxParameters, final Map<String, Object> requestLocationParameters, final TargetCallback<String> callback);
      ```

   * **Retorna**: N/A

   * **Parâmetros:**

      Estes são os parâmetros para este método:

      * **name**

         Nome da mbox/localização do Target que você quer recuperar.

         * **Tipo:** cadeia de caracteres
      * **defaultContent**

         O valor retornado no retorno de chamada se não for possível alcançar o servidor do Target, ou se o usuário não estiver qualificado para a campanha.

         * **Tipo:** cadeia de caracteres
      * **profileParameters**

         Os valores neste dicionário serão adicionados ao objeto &quot;profileParameters&quot; na solicitação para o Target.

         * **Tipo:** mapa `<String, Object>`
      * **orderParameters**

         Os valores neste dicionário serão adicionados ao objeto &quot;order&quot; na solicitação para o Target.

         * **Tipo:** mapa `<String, Object>`
      * **mboxParameters**

         Os valores neste dicionário aparecerão na solicitação para o Target.

         * **Tipo:** mapa `<String, Object>`
      * **requestLocationParameters**

         Os valores neste dicionário serão adicionados ao objeto &quot;requestLocation&quot; na solicitação para o Target.

         * **Tipo:** mapa `<String, Object>`
      * **callback**

         Este método será chamado com o conteúdo da oferta do servidor Target. Se não for possível alcançar o servidor do Target ou se o usuário não for qualificado para a campanha, defaultContent será retornado.

         * **Tipo:** TargetCallback `<String>`
   * Esta é uma amostra de código para este método:

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put("profile-parameter-key", "profile-parameter-value"); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put("order-parameter-key", "order-parameter-value"); 
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); mboxParameters.put("mbox-parameter-key", "mbox-parameter-value"); 
      Map `<String, Object>` requestLocationParameters = new HashMap `<String, Object>`(); requestLocationParameters.put("request-location-parameter-key", "request-location-parameter-value"); 
      
      Target.loadRequest("mboxName", "defaultContent", profileParameters, orderParameters, mboxParameters, requestLocationParameters,new TargetCallback<String>() {
         @Override
         public void call (String item) { 
            Log.d("Target Content", item);
         } 
      });
      ```

      Para obter mais informações sobre a API subjacente do Target, consulte [Carregar solicitações do Target](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-target/target-api-reference-deprecated#load-target-requests) na referência da API do Target.








* **createOrder&#x200B;ConfirmRequest**

   Cria um objeto TargetLocationRequest com os parâmetros fornecidos.

   * Esta é a sintaxe para este método:

      ```java
      public static TargetLocationRequest createOrderConfirmRequest(String name, String orderId, String orderTotal, String productPurchasedId, Map<String, Object> parameters);
      ```

   * Esta é a amostra de código para este método:

      ```java
      TargetLocationRequest orderConfirm = Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null);
      ```

* **createRequest**

   Cria um objeto TargetLocationRequest com os parâmetros fornecidos.

   * Esta é a sintaxe para este método:

      ```java
      public static TargetLocationRequest createRequest(String name, String defaultContent, Map<String, Object> parameters);
      ```

   * Esta é a amostra de código para este método:

      ```java
      TargetLocationRequest heroBannerRequest = Target.createRequest("heroBanner", "default.png", null);
      ```

* **clearCookies**

   Apaga quaisquer cookies de destino do seu aplicativo.

   * Esta é a sintaxe para este método:

      ```java
      public static void clearCookies();
      ```

   * Esta é a amostra de código para este método:

      ```java
      Target.clearCookies();
      ```

* **getPcID**

   Retorna a pcID.

   * Esta é a sintaxe para este método:

      ```java
      public static String getPcID();
      ```

   * Esta é a amostra de código para este método:

      ```java
      Target.getPcID();
      ```

* **getSessionID**

   Retorna a ID da sessão.

   * Esta é a sintaxe para este método:

      ```java
      public static String getSessionID();
      ```

   * Esta é a amostra de código para este método:

      ```java
      Target.getSessionID();
      ```

* **setThirdPartyID**

   Define a ID de terceiros.

   * Esta é a sintaxe para este método:

      ```java
      public static String setThirdPartyID(final String thirdPartyId);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Target.setThirdPartyID("third-party-id");
      ```

* **getThirdPartyID**

   Retorna a ID de terceiros.

   * Esta é a sintaxe para este método:

      ```java
      public static String getThirdPartyID();
      ```

   * Esta é a amostra de código para este método:

      ```java
      String thirdPartyId = Target.getThirdPartyID();
      ```
