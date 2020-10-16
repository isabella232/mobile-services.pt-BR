---
description: A partir do Android SDK versão 4.5, uma nova extensão do Android permite coletar dados do seu aplicativo Android Wearable.
seo-description: A partir do Android SDK versão 4.5, uma nova extensão do Android permite coletar dados do seu aplicativo Android Wearable.
seo-title: Android Wearables  Introdução
solution: Experience Cloud,Analytics
title: Android Wearables  Introdução
topic: Developer and implementation
uuid: bfe5d41e-b17c-4634-80ac-7a38671ecb81
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '291'
ht-degree: 100%

---


# Android Wearables: introdução {#android-wearables-getting-started}

A partir do Android SDK versão 4.5, uma nova extensão do Android permite coletar dados do seu aplicativo Android Wearable.

## Configuração do SDK para um aplicativo handheld (Android Studio) {#section_262237484EC44C58953891B105F0D000}

Para obter mais informações sobre como importar o SDK para o seu projeto, consulte [Implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Adicione o arquivo `ADBMobileConfig.json` à pasta de assets do projeto.
1. Adicione o arquivo `adobeMobileLibrary-*.jar` à pasta libs ou certifique-se de que ele esteja referenciado no projeto.

   >[!TIP]
   >
   >Talvez seja necessário sincronizar o projeto gradle após adicionar o arquivo `.jar`.

1. No método `onCreate`, permita o acesso do SDK ao contexto do aplicativo usando o `Config.setContext`:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext()); 
   }
   ```

1. Adicione o seguinte código ao arquivo `AndroidManifest.xml`:

   ```java
       <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> 
       <uses-permission android:name="android.permission.INTERNET" /> 
       <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. Certifique-se de que o projeto inclua a biblioteca de serviços do Google Play.
1. Implemente `WearableListenerService` ou adicione o código correspondente a `WearableListenerService`:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onMessageReceived(MessageEvent messageEvent) { 
           super.onMessageReceived(messageEvent); 
       } 
   
       private GoogleApiClient mGoogleApiClient; 
   
       @Override 
       public void onCreate() { 
           super.onCreate(); 
           mGoogleApiClient = new GoogleApiClient.Builder(this) 
                   .addApi(Wearable.API) 
                   .build(); 
           mGoogleApiClient.connect(); 
       } 
       @Override 
       public void onDestroy() { 
           super.onDestroy(); 
           mGoogleApiClient.disconnect(); 
       } 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerHandheld.onDataChanged(dataEvents, mGoogleApiClient, this); 
       } 
   }
   ```

1. Adicionar `WearListenerService` ao arquivo `AndroidManifest.xml`:

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

## Configuração do SDK para um aplicativo Wearable (Android Studio) {#section_2268EC03E20B4A228A28BDCFEA2E9AE4}

1. Conclua uma das seguintes tarefas:

   * Adicione o mesmo arquivo `ADBMobileConfig.json` à pasta de ativos do projeto wearable.
   * Altere a configuração de gradle para usar `ADBMobileConfig.json` na pasta de ativos do aplicativo portátil:

      ```java
      android { 
      
          sourceSets { 
              main { 
                  assets.srcDirs = ['src/main/assets','../mobile/src/main/assets'] 
              } 
         } 
      }
      ```

1. Adicione o arquivo `adobeMobileLibrary-*.jar` à pasta libs ou verifique se está referenciado no projeto.

   Talvez seja necessário sincronizar o projeto gradle após adicionar o arquivo jar.

1. No método `onCreate`, permita o acesso do SDK ao contexto do aplicativo usando `Config.setContext`:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main);      
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext(), Config.ApplicationType.APPLICATION_TYPE_WEARABLE); 
   }
   ```

1. Adicione o código a seguir a `AndroidManifest.xml`:

   ```java
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. Certifique-se de que o projeto inclua a biblioteca de serviços do Google Play.
1. Implemente `WearableListenerService` ou adicione o código correspondente a `WearableListenerService`:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerWearable.onDataChanged(dataEvents); 
       } 
   
   }
   ```

1. Adicionar `WearListenerService` ao arquivo `AndroidManifest.xml`:

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

