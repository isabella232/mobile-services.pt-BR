---
description: Aqui estão os métodos do Serviço da Experience Cloud ID fornecidos pela biblioteca do Android.
keywords: android;library;mobile;sdk
seo-description: Aqui estão os métodos do Serviço da Experience Cloud ID fornecidos pela biblioteca do Android.
seo-title: Métodos do Adobe Experience Platform Identity Service
solution: Marketing Cloud,Analytics
title: Métodos do Adobe Experience Platform Identity Service
topic: Developer and implementation
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# Métodos do Adobe Experience Platform Identity Service{#experience-cloud-id-service-methods}

Aqui estão os métodos do Serviço da Experience Cloud ID fornecidos pela biblioteca do Android.

Atualmente, o SDK é compatível com várias soluções da Adobe Experience Cloud, incluindo o Analytics, o Target, o Audience Manager e o Adobe Experience Platform Identity Service.

Os métodos recebem o prefixo de acordo com a solução. Por exemplo, métodos da Experience Cloud ID recebem o prefixo `visitor`. Para obter mais informações, consulte [Configuração da Experience Cloud ID](/help/android/c-marketing-cloud/mcvid.md).

* **public static String appendToURL(final String URL)**

   Acrescenta dados de visitantes da Adobe a uma cadeia de caracteres de URL para uso com a biblioteca JavaScript da Adobe. É necessário ter o Mobile SDK 4.12+ para usar esse método. Para obter mais informações, consulte [Anexar função de ajuda da ID de visitante](https://docs.adobe.com/content/help/pt-BR/id-service/using/id-service-api/methods/appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Este método pode causar uma chamada de rede de bloqueio. Não chame este método em tópicos sensíveis ao tempo.

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
      >Este método pode causar uma chamada de bloqueio de rede e **não** deve ser chamado de um encadeamento da interface do usuário.

* **syncIdentifiers**

   Com a Experience Cloud ID, é possível definir outras IDs do cliente que podem ser associadas a cada visitante. A API do Visitante aceita várias IDs do cliente para o mesmo visitante, com um identificador de tipo de cliente para separar o escopo de diferentes IDs do cliente. Este método corresponde a `setCustomerIDs` na biblioteca do JavaScript.

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

   Introduzido na versão 4.16.0, este método retorna uma sequência de caracteres devidamente formada que contém variáveis de URL do Serviço de ID de visitante. Para obter mais informações sobre como esse método é usado, consulte [Métodos do Adobe Experience Platform Identity Service](/help/android/reference/hybrid-app.md).

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

## Métodos públicos {#section_8AC744B431A3438C9B45629CA3EA0F51}

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
