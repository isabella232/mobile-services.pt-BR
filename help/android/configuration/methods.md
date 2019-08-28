---
description: Esta é uma lista de métodos do fornecida pela biblioteca do Android.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: Esta é uma lista de métodos do fornecida pela biblioteca do Android.
seo-title: Configuração de métodos
solution: Marketing Cloud, Analytics
title: Configuração de métodos
topic: Desenvolvedor e implementação
uuid: 663 aeb 6 c -1 b 97-4 a 3 a -8 c 0 e-dd 4 c 2 ec 28 c 01
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Configuration methods{#configuration-methods}

Esta é uma lista de métodos do fornecida pela biblioteca do Android.

## Initial configuration {#section_9169243ECC4744A899A8271F92090ECD}

O método a seguir deve ser chamado uma vez no método `onCreate` da atividade principal:

* `setContext`
Esta é a amostra de código para este método:

   ```java
    @Override
    public void onCreate(BundlesavedInstanceState){
      super.onCreate(savedInstanceState)
      setContentView(R.layout.main);
      Config.setContext(this.getApplicationContext());
    }
   ````


## SDK settings (Config Class) {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **registerAdobeDataCallback**

   * Registra um objeto que implementa a interface do `AdobeDataCallback`. The overwritten "call" method will be invoked with a `Config.MobileDataEvent` value and the associated data in a `Map<String, Object>` for the triggering event. Para obter mais detalhes sobre quais eventos acionarão esse retorno de chamada, consulte *mobiledataeventenum* na parte inferior deste tópico.

      >[!TIP]
      >
      >Esse método requer a versão 4.9.0 ou posterior.

   * Esta é a sintaxe para este método:

      ```java
      public static void registerAdobeDataCallback(final AdobeDataCallback&amp;nbsp;callback);
      ```

   * Esta é a amostra de código para este método:

      ```java
        Config.registerAdobeDataCallback(new Config.AdobeDataCallback() {
          @Override
          public void call(Config.MobileDataEvent event, Map<String, Object> contextData) {
              // handle each event type accordingly 
              if (event == Config.MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL) {
                   // do something with acquisition data found in contextData parameter
                   HashMap<String, Object> acquisitionData = new HashMap<String, Object>(contextData);
              }
          }
      });
      ```

* **getVersion**

   * Retorna a versão atual da biblioteca do Adobe Mobile.
   * Esta é a sintaxe para este método:

      ```java
      public static String getVersion();
      ```

   * Este é um exemplo de código para este método:

      ```java
      String libraryVersion = Config.getVersion(); 
      ```

* **getPrivacyStatus**

   * Retorna a representação de enumeração do status de privacidade do usuário atual.

      Estes são os valores do status de privacidade:

      * `MOBILE_PRIVACY_STATUS_OPT_IN`, onde as ocorrências são enviadas imediatamente.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`, onde são descartados.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`, se o conjunto de relatórios tiver um carimbo de hora e data, as ocorrências serão salvas até que o status de privacidade seja alterado para opt-in (as ocorrências são enviadas) ou opt-out (as ocorrências são descartadas).

         Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in. O valor padrão está definido no arquivo `ADBMobileConfig.json`.
   * Esta é a sintaxe para este método:

      ```java
      public static MobilePrivacyStatus getPrivacyStatus(); 
      ```

   * Esta é uma amostra de código para este método:

      ```java
      MobilePrivacyStatus privacyStatus Config.getPrivacyStatus();
      ```


* **setPrivacyStatus**

   * Define o de privacidade do usuário atual como `status`status.

      E possível definir o status de privacidade para um dos valores a seguir:
      * `MOBILE_PRIVACY_STATUS_OPT_IN`, onde as ocorrências são enviadas imediatamente. Essas ocorrências são enviadas imediatamente.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`, onde são descartados. Essas ocorrências são descartadas.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`, se o conjunto de relatórios tiver um carimbo de hora e data, as ocorrências serão salvas até que o status de privacidade seja alterado para opt-in (as ocorrências são enviadas) ou opt-out (as ocorrências são descartadas).
Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.
   * Esta é a sintaxe para este método:

      ```java
      public static void setPrivacyStatus(MobilePrivacyStatus status); 
      ```

   * Esta é uma amostra de código para este método:

      ```java
      Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
      ```


* **getLifetimeValue**

   * Retorna o valor do tempo de vida do usuário atual. O valor padrão é `0`.

   * Esta é a sintaxe para este método:

      ```java
      public static BigDecimal getLifetimeValue();
      ```

   * Esta é uma amostra de código para este método:

      ```java
      BigDecimal currentLifetimeValue Config.getLifetimeValue(); 
      ```

* **getUserIdentifier**

   * Se um identificador personalizado do usuário foi definido, ele é retornado. Se um identificador personalizado não foi definido, retorna `null`. O valor padrão é `null`.

      >[!TIP]
      >
      >Se o aplicativo for atualizado do Experience Cloud 3. x para o SDK 4. x, a ID de visitante personalizada ou gerada automaticamente anterior será recuperada e armazenada como o identificador do usuário personalizado. Isso preserva os dados dos visitantes entre as atualizações de SDK. Para novas instalações do SDK 4.x, até que seja definido, o identificador do usuário é `null`.

   * Esta é a sintaxe para este método:

      ```java
      public static String&amp getUserIdentifier();
      ```

   * Aqui, a amostra de código para este método:

      ```java
      String userId = Config.getUserIdentifier();
      ```

* **setUserIdentifier**

   * Define o identificador do usuário para `identifier`.
   * Esta é a sintaxe para este método:

      ```java
      public static void setUserIdentifer(String identifier);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Config.setUserIdentifier("billybob"); 
      ```

* **getDebugLogging**

   * Retorna a preferência de log para a depuração atual. O valor padrão é `false`.
   * Esta é a sintaxe para este método:

      ```java
      public static Boolean getDebugLogging(); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Boolean debugging = Config.getDebugLogging(); 
      ```

* **setDebugLogging**
   * Define a preferência do log de depuração como `debugLogging`.
   * Esta é a sintaxe para este método:

      ```java
      public static void setDebugLogging(Boolea debugLogging);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Config.setDebugLogging(true);
      ```

* **collectLifecycleData**
   * Indica ao SDK que os dados do ciclo de vida devem ser coletados para uso em todas as soluções no SDK. Para obter mais informações, consulte [Medições de ciclo de vida](/help/android/configuration/methods.md).

   * Esta é a sintaxe para este método:

      ```java
      public static void collectLifecycleData(final Activity activity,final Map<String, Object>contextData); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      @Override
      protectedvoid  onResume()  {
        super.onResume();
        Config.collectLifecycleData(this);
        } 
      ```

      Com dados de contexto extras:

      ```java
      @Override
      public  void  onResume()  {
        HashMap<String, Object> contextData = new HashMap<String, Object>();
        contextData.put("myapp.category", "Game");        Config.collectLifecycleData(this, contextData);} 
      ```

* **collectLifecycleData (atividade Activity)**

   * (**Versão 4.2 ou superior**) Indica ao SDK que os dados do ciclo de vida devem ser coletados para uso em todas as soluções no SDK. Para obter mais informações, consulte [Medições de ciclo de vida](/help/android/metrics.md).
   * Esta é a sintaxe para este método:

      ```java
      public static void collectLifecycleData(final Activity activity);
      ```

   * Esta é a amostra de código para este método:

      ```java
      @Overrideprotected void onResume() {
        super.onResume()
        // assume being called in an Activity class Config.collectLifecycleData(this);
        } 
        ```
      
* **pauseCollecting&#x200B;LifecycleData**

   * Indica ao SDK que o aplicativo está pausado, a fim de calcular corretamente as medições de ciclo de vida. Por exemplo, o `onPause` coleta um carimbo de data e hora para determinar a duração da sessão anterior. Isso também define um sinalizador para que o ciclo de vida saiba que o aplicativo não parou de funcionar. Para obter mais informações, consulte [Medições de ciclo de vida](/help/android/metrics.md).

   * Esta é a sintaxe para este método:

      ```java
      public static void pauseCollectingLifecycleData(); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      @Override
      protected void onPause() {
        super.onPause();
        Config.pauseCollectingLifecycleData();
      } 
      ```

* **setSmallIconResourceId(int resourceId)**

   * (**Versão 4.2 ou superior**) Define o ícone pequeno que será usado nas notificações criadas pelo SDK. Este ícone aparecerá na barra de status e será a imagem secundária exibida quando o usuário visualizar a notificação completa na central de notificações.
   * Esta é a sintaxe para este método:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **setLargeIconResourceId(int resourceId)**

   * (**Versão 4.2 ou superior**) Define o ícone grande que será usado nas notificações criadas pelo SDK. Este ícone será a principal imagem exibida quando o usuário visualizar a notificação completa na central de notificações.
   * Esta é a sintaxe para este método:

      ```java
      public static void setLargeIconResourceId(final int  resourceId);
      ```

   * Esta é a amostra de código para este método:

      ```Java
      Config.setLargeIconResourceId(R.drawable.appIcon);
      ```

* **overrideConfigStream(InputStream configInput)**

   * (**Versão 4.2 ou superior**) Permite carregar um arquivo de configuração ADBMobile JSON diferente quando o aplicativo é iniciado. A configuração diferente é utilizada até o aplicativo ser fechado.
   * Esta é a sintaxe para este método:

      ```java
      public static void overrideConfigStream(final InputStream configInput);
      ```

   * Esta é a amostra de código para este método:

      ```java
       try {
          InputStream configInput = getAssets().open("ExampleJSONFile.json") 
          Config.overrideConfigStream(configInput)
          } catch (IOException ex) { 
          //do something with the exception if needed
      }
      ```

* **setPushIdentifier**

   * Define o token do dispositivo para notificações por push.
   * Esta é a sintaxe para este método:

      ```java
      public static void setPushIdentifier(final String registrationId); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ...// note the code to retreive the push token must run in the background
      InstanceID instanceID= InstanceID.getInstance(getApplicationContext());String token=instanceID.getToken("835015092242", GoogleCloudMessaging.INSTANCE_ID_SCOPE null);Config.setPushIdentifier(token);
      ...
      ```

* **submitAdvertisingIdentifierTask**

   * Fornece um Callable ao SDK que retorna a string do Identificador de anúncio retornado do Google Play Services. O SDK executa esta tarefa em um encadeamento em segundo plano e define uma variável interna para o Identificador de anúncio baseada no valor retornado do Callable.

      >[!IMPORTANT]
      > 
      >If you want to use the Advertising Identifier in Acquisition or Lifecycle, call it before calling `Config.collectLifecycleData`.

      * Esta é a sintaxe para este método:

         ```java
         public static void submitAdvertisingIdentifierTask(final Callable<String> task); 
         ```

      * Esta é a amostra de código para este método:

         ```java
         @Override
         public void  onResume() {
             super.onResume();
             final  Callable<String>; task = new Callable<String>(){
                 @Override
                 public String call() throws Exception {
                    AdvertisingIdClient.Info idInfo;
                    String adid = null;
                    Context appContext = CLASSNAME.this.getApplicationContext();
                    try {
                         idInfo = AdvertisingIdClient.getAdvertisingIdInfo(appContext);
                         if (idInfo != null) { 
                             adid = idInfo.getId();
                         } 
                    } catch  (Exception ex) {
                        Log.e("Error",  ex.getLocalizedMessage());
                    }
                    return  adid;
                 }
           };
           Config.submitAdvertisingIdentifierTask(task); 
           Config.collectLifecycleData(this);
         }
         ```


## Interface do AdobeDataCallback {#section_600A63B3136F47DCB928071485C5117C}

```java
public interface AdobeDataCallback {  
    void call(MobileDataEvent event, Map<String, Object> contextData);  
} 
```

## MobileDataEvent Enum {#section_92732814141646E294782BC9020367EB}

```java
public enum MobileDataEvent {  
    MobileDataEvent.MOBILE_EVENT_LIFECYCLE, // triggers on a lifecycle hit  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL, // triggers on a app install that has acquisition data  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH // triggers on launch when the device previously installed via acquisition  
}
```
