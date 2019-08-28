---
description: Esta é uma lista de métodos do Adobe Target fornecida pela biblioteca do Android.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: Esta é uma lista de métodos do Adobe Target fornecida pela biblioteca do Android.
seo-title: Métodos do Target para Android
solution: Marketing Cloud, Analytics
title: Métodos do Target para Android
topic: Desenvolvedor e implementação
uuid: 8 e 9808 b 2-ba 80-4646-ba 05-8 e 62 d 4 fde 065
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Métodos do Target para Android{#target-methods}

Esta é uma lista de métodos do Adobe Target fornecida pela biblioteca do Android.

O SDK suporta atualmente várias Soluções da Adobe Experience Cloud, incluindo o Analytics, o Target, o Audience Manager e o Adobe Experience Platform Identity Service]. Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `target`.

>[!TIP]
>
>[Medições de ciclo de vida](/help/android/metrics.md) são enviadas como parâmetros para cada carregamento de mbox.

## Class reference : TargetLocationRequest {#section_A8CC898922164E819EC730DC92A6742B}

**Propriedades:**

```java
public String name; 
public String defaultContent; 
public HashMap<String, Object> parameters;
```

**Constantes da string**

>[!TIP]
>
>As constantes a seguir são para facilitar o uso quando você define chaves para parâmetros personalizados.

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
>* If you are using SDKs **before** version 4.14.0, see [https://developers.adobetarget.com/api/#input-parameters](https://developers.adobetarget.com/api/#input-parameters) for parameters limitations.
   >
   >
* If you are using SDKs version 4.14.0 **or later**, see [https://developers.adobetarget.com/api/#batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters) for parameters limitations.


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
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”);
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); 
      mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters
      new TargetCallback<String>() {
          @Override
          public void call (String item) {
             Log.d(“Target Content”, item); 
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

         * **Tipo:** String
      * **defaultContent**

         O valor retornado no retorno de chamada se não for possível alcançar o servidor do Target, ou se o usuário não estiver qualificado para a campanha.

         * **Tipo:** String
      * **profileParameters**

         Os valores neste dicionário serão adicionados ao objeto "profileParameters" na solicitação para o Target.

         * **Tipo:** Mapa `<String, Object>`
      * **orderParameters**

         Os valores neste dicionário serão adicionados ao objeto "order" na solicitação para o Target.

         * **Tipo:** Mapa `<String, Object>`
      * **mboxParameters**

         Os valores nesse dicionário aparecerão na solicitação para o Target.

         * **Tipo:** Mapa `<String, Object>`
      * **requestLocationParameters**

         Os valores neste dicionário serão adicionados ao objeto "requestLocation" na solicitação para o Target.

         * **Tipo:** Mapa `<String, Object>`
      * **callback**

         Este método será chamado com o conteúdo da oferta do servidor Target. Se não for possível alcançar o servidor do Target ou se o usuário não for qualificado para a campanha, defaultContent será retornado.

         * **Tipo:** Targetcallback `<String>`
   * Este é um exemplo de código para este método:

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”); 
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Map `<String, Object>` requestLocationParameters = new HashMap `<String, Object>`(); requestLocationParameters.put(“request-location-parameter-key”, “request-location-parameter-value”); 
      
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters, requestLocationParameters,new TargetCallback<String>() {
         @Override
         public void call (String item) { 
            Log.d(“Target Content”, item);
         } 
      });
      ```

      Para obter mais informações sobre a API subjacente do Target, consulte [Entrega](https://docs.adobe.com/dev/products/target/reference/delivery.html) na ajuda do desenvolvedor do Target.








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
      Target.setThirdPartyID(“third-party-id”);
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
