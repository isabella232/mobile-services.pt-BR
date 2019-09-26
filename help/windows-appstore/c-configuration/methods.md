---
description: Classes e métodos fornecidos pela biblioteca da loja universal de aplicativos do Windows 8.1.
seo-description: Classes e métodos fornecidos pela biblioteca da loja universal de aplicativos do Windows 8.1.
seo-title: SDK methods
solution: Marketing Cloud,Analytics
title: Métodos do SDK
topic: Desenvolvedor e implementação
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2cea
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

Classes e métodos fornecidos pela biblioteca da loja universal de aplicativos do Windows 8.1.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **GetVersion (winJS: getVersion)**

   Retorna a versão atual da biblioteca do Adobe Mobile.

   * Esta é a sintaxe para este método:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Esta é a amostra de código para este método:

      ```js
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **GetPrivacyStatusAsync (winJS: getPrivacyStatusAsync)**

   Retorna a representação de enumeração do status de privacidade do usuário atual.

   * `ADBMobilePrivacyStatusOptIn` - as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut` - as ocorrências serão descartadas.
   * `ADBMobilePrivacyStatusUnknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para opt-in (as ocorrências são enviadas) ou opt-out (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

      The default value is set in the [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md) file.

   * Esta é a sintaxe para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * Estas são as amostras de código para este método:

      ```csharp
      public enum class ADBMobilePrivacyStatus : int  {
        ADBMobilePrivacyStatusOptIn = 1, 
        ADBMobilePrivacyStatusOptOut =  2,
        ADBMobilePrivacyStatusUnknown = 3
      };
      ```

      ```js
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
      status = privacyStatus;
      }); 
      ```

* **SetPrivacyStatus (winJS: setPrivacyStatus)**

   Define o de privacidade do usuário atual como `status`status. É definido como um dos valores abaixo:

   * `ADBMobilePrivacyStatusOptIn` - as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut` - as ocorrências serão descartadas.
   * `ADBMobilePrivacyStatusUnknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para opt-in (as ocorrências são enviadas) ou opt-out (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

   * Esta é a sintaxe para este método:

      ```csharp
      static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Esta é a amostra de código para este método:

      ```csharp
      public enum class ADBMobilePrivacyStatus : int {
        ADBMobilePrivacyStatusOptIn = 1,
        ADBMobilePrivacyStatusOptOut = 2,
        ADBMobilePrivacyStatusUnknown = 3
        }; 
      ```

      ```js
      var ADB = ADBMobile;
      ADB.Config.setPrivacyStatus(ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn); 
      ```

* **GetLifetimeValue (winJS: getLifetimeValue)**

   Retorna o valor do tempo de vida do usuário atual. O padrão é 0.

   * Esta é a sintaxe para este método:

      ```csharp
      static float GetLifetimeValue();
      ```

   * Esta é a amostra de código para este método:

      ```js
       var ADB = ADBMobile;
       var ltv = ADB.Config.getLifetimeValue(); 
      ```

* **GetUserIdentifier (winJS: getUserIdentifier)**

   Retorna o identificador do usuário personalizado se algum estiver configurado. Retorna nulo se um identificador personalizado não estiver configurado. O valor padrão é `null`.

   >[!TIP]
   >
   >Se seu aplicativo for atualizado do SDK 3.x da Experience Cloud para o 4.x, a ID anterior (personalizada ou gerada automaticamente) será recuperada e armazenada como o identificador personalizado do usuário. Isso preserva os dados do visitante entre as atualizações de SDK. Para novas instalações do SDK 4.x, o identificador de usuário é `null` até que seja definido.

   * Esta é a sintaxe para este método:

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier (winJS: setUserIdentifier)**

   Define o identificador do usuário para `identifier`.

   * Esta é a sintaxe para este método:

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier);
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId"); 
      ```

* **GetDebugLogging (winJS: getDebugLogging)**

   Retorna a preferência de log para a depuração atual. O valor padrão é `false`.

   * Esta é a sintaxe para este método:

      ```csharp
      static bool GetDebugLogging(); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging(); 
      ```

* **SetDebugLogging (winJS: setDebugLogging)**

   Define a preferência do log de depuração como `debugLogging`. O registro de depuração funciona apenas ao usar a versão de depuração da biblioteca, a versão de lançamento ignora esta configuração.

   * Esta é a sintaxe para este método:

      ```csharp
      static void SetDebugLogging(bool debugLogging); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true); 
      ```

* **CollectLifecycleData (winJS: collectLifecycleData)**

   Indica ao SDK que os dados do ciclo de vida devem ser coletados para uso em todas as soluções no SDK. Para obter mais informações, consulte [Medições de ciclo de vida](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Invoke this method in the `onResume()` method in each Activity inside of your application, as shown in the following example. Recomendamos transferir a Atividade ou o Serviço como o objeto de contexto em vez do contexto de Aplicativo global.

   * Esta é a sintaxe para este método:

      ```csharp
      static void CollectLifecycleData();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData(); 
      ```

* **PauseCollecting &#x200B; LifecycleData (winJS: pauseCollecting &#x200B; LifecycleData)**

   Indica ao SDK que o aplicativo está pausado, a fim de calcular corretamente as métricas de ciclo de vida. Por exemplo, durante a pausa um carimbo de data e hora é coletado para determinar a duração da sessão anterior. Também define um sinalizador para que o ciclo de vida saiba que o aplicativo não parou de funcionar. Para obter mais informações, consulte [Medições de ciclo de vida](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Invoke this method in the `onPause()` methods in each Activity inside Your application, as shown in the example. Recomendamos transferir a Atividade ou o Serviço como o objeto de contexto em vez do contexto de Aplicativo global.

   * Esta é a sintaxe para este método:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
