---
description: Aqui estão os métodos do Serviço da Experience Cloud ID fornecidos pela biblioteca do Android.
keywords: android;biblioteca;móvel;sdk
seo-description: Aqui estão os métodos do Serviço da Experience Cloud ID fornecidos pela biblioteca do Android.
seo-title: Adobe Experience Platform Identity Service methods
solution: Marketing Cloud,Analytics
title: Métodos do Adobe Experience Platform Identity Service
topic: Desenvolvedor e implementação
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
translation-type: tm+mt
source-git-commit: 8fc515a6e89044b9dac98b3f207c5f43b658a2ec

---


# Adobe Experience Platform Identity Service methods{#experience-cloud-id-service-methods}

Aqui estão os métodos do Serviço da Experience Cloud ID fornecidos pela biblioteca do Android.

The SDK currently supports multiple Adobe Experience Cloud Solutions], including Analytics, Target, Audience Manager, and the Adobe Experience Platform Identity Service.

Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `visitor`. For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).

* **public static String appendToURL(final String URL)**

   Anexa os dados de visitante da Adobe a uma cadeia de caracteres do URL para usar com a biblioteca do Adobe JavaScript. É necessário ter o Mobile SDK 4.12+ para usar esse método. Para obter mais informações, consulte [Anexar função de ajuda da ID de visitante](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html).

   >[!IMPORTANT]
   >
   >This method can cause a blocking network call. Não chame este método em tópicos sensíveis ao tempo.

   * Esta é a sintaxe para este método:

      ```java
      public static String appendToURL(final String URL) 
      ```

      Uma string obrigatória com o URL à qual as informações do visitante serão anexadas.

   * Esta é a amostra de código para este método:

      ```java
      String urlSample = "https://example.com";`
              String urlWithAdobeVisitorInfo = Visitor.appendToURL(urlSample);
      
              Intent(Intent.ACTION_VIEW);
              i.setData(Uri.parse(urlWithAdobeVisitorInfo));
              startActivity(i);
      ```

* **getMarketingCloudId**

   Recupera a Experience Cloud ID a partir do serviço de ID de visitante.

   * Esta é a sintaxe para este método:

      ```java
      public static String getMarketingCloudId(); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      String = Visitor.getMarketingCloudId();
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **syncIdentifiers**

   Com a Experience Cloud ID, é possível definir IDs adicionais de clientes que podem ser associadas a cada visitante. A API de visitante aceita várias IDs do cliente para o mesmo visitante, junto com um identificador de tipo de cliente para separar o escopo de diferentes IDs do cliente. Este método corresponde a `setCustomerIDs` na biblioteca do JavaScript.

   * Esta é a sintaxe para este método:

      ```java
      public static void syncIdentifiers(Map<String, String> identifiers); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Map<String,String> identifiers = new HashMap<String, String>();
      identifiers.put("idType", "idValue");
      Visitor.syncIdentifiers(identifiers);
      ```

* **syncIdentifier**

   Sincroniza o tipo de identificador fornecido e o valor para o serviço de ID do visitante.

   Transmite `authenticationState` como um dos seguintes valores:

   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * Esta é a sintaxe para este método:

      ```java
      public static void syncIdentifier(final String identifierType, final String identifier, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Visitor.syncIdentifier("myIdType", "valueForUser", VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT);
      ```

* **syncIdentifiers**

   Sincroniza os identificadores fornecidos ao serviço de ID.

   Transmite `authenticationState` como um dos seguintes valores:
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * Esta é a sintaxe para este método:

      ```java
      public static void syncIdentifiers(final Map<String String> identifiers, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Map<String, String> identifiers = new HashMap<String, String>();
          identifiers.put("myIdType", "valueForUser"); Visitor.syncIdentifiers(identifiers,
      VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED); 
      ```

* **getIdentifiers**

   Recupera uma lista de objetos `ADBVisitorID` de somente leitura.

   * Esta é a sintaxe para este método:

      ```java
      public static List<VisitorID> getIdentifiers(); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      List<VisitorID> myVisitorIDs = Visitor.getIdentifiers(); 
      ```

* **getUrlVariablesAsync**

   Introduzido na versão 4.16.0, este método retorna uma sequência de caracteres devidamente formada que contém variáveis de URL do Serviço de ID de visitante. For more information about how this method is used, see Adobe Experience Platform Identity Service methods.[](/help/android/reference/hybrid-app.md)

   * Esta é a sintaxe para este método:

      ```java
      public static void getUrlVariablesAsync(final VisitorCallback callback);
      ```

   * Esta é a amostra de código para este método:

      ```java
      final String urlString = https://www.mydomain.com/index.php; 
      Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
        @Override 
        public void call(String urlVariables) { 
            final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
            ...
        } 
      });
      ```

## Public methods {#section_8AC744B431A3438C9B45629CA3EA0F51}

```java
public class VisitorID { 
    public final String idOrigin; 
    public final String idType; 
    public final String id; 
    public VisitorIDAuthenticationState authenticationState; 
 
    public enum VisitorIDAuthenticationState { 
         VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN(0), 
         VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED(1), 
         VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT(2); 
    } 
}
```
