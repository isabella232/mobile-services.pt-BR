---
description: Classes e métodos fornecidos pela biblioteca da plataforma Universal Windows.
seo-description: Classes e métodos fornecidos pela biblioteca da plataforma Universal Windows.
seo-title: Métodos do SDK
solution: Marketing Cloud,Analytics
title: Métodos do SDK
topic: Developer and implementation
uuid: e3aa41d6-7bc0-4208-a662-12907c209a77
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 66%

---


# SDK methods {#sdk-methods}

Classes e métodos fornecidos pela biblioteca da plataforma Universal Windows.

>[!TIP]
>
>Quando você consome `winmd` métodos do winJS (JavaScript), todos os métodos têm automaticamente a primeira letra em minúsculas.

* **GetVersion (winJS: getVersion)**

   Retorna a versão atual da biblioteca do Adobe Mobile.

   * Esta é a sintaxe para este método:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **GetPrivacyStatusAsync (winJS: getPrivacyStatusAsync)**

   Retorna a representação de enumeração do status de privacidade do usuário atual.

   * `ADBMobilePrivacyStatusOptIn` - as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut` - as ocorrências são descartadas.
   * `ADBMobilePrivacyStatusUnknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

      The default value is set in the `ADBMobileConfig.json` config file. Para obter mais informações, consulte o arquivo [de configuração](/help/universal-windows/c-configuration/c.json.md)ADBMobileConfig.json.

   * Esta é a sintaxe para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * Estas são as amostras de código para este método:

      **C Sharp**

      ```csharp
      public enum class ADBMobilePrivacyStatus : int { ADBMobilePrivacyStatusOptIn = 1, 
      ADBMobilePrivacyStatusOptOut = 2, 
      ADBMobilePrivacyStatusUnknown = 3};
      ```

      **JavaScript**

      ```javascript
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
        status = privacyStatus;}
      );
      ```

* **SetPrivacyStatus (winJS: setPrivacyStatus)**

   Define o de privacidade do usuário atual como `status`status. É definido como um dos valores abaixo:
   * `ADBMobilePrivacyStatusOptIn` - as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut` - as ocorrências serão descartadas.
   * `DBMobilePrivacyStatusUnknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas. Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

      * Esta é a sintaxe para este método:

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * Estas são as amostras de código para este método:

         **C-shark**

         ```csharp
         public enum class ADBMobilePrivacyStatus : int { 
           ADBMobilePrivacyStatusOptIn = 1, 
           ADBMobilePrivacyStatusOptOut = 2
           ADBMobilePrivacyStatusUnknown = 3
         };
         ```

         **JavaScript**

         ```js
         var ADB = ADBMobile;
         ADB.Config.setPrivacyStatus (ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn
         );
         ```

* **GetLifetimeValue (winJS: getLifetimeValue)**

   Retorna o valor do tempo de vida do usuário atual. O valor padrão é `0`.

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

   Retorna o identificador de usuário personalizado se um identificador personalizado tiver sido definido. Returns `null` if a custom identifier is not set.
O valor padrão é `null`.

   >[!IMPORTANT]
   >
   >Se seu aplicativo for atualizado do SDK Experience Cloud 3.x para 4.x, o serviço de ID anterior (personalizado ou gerado automaticamente) será recuperado e armazenado como o identificador de usuário personalizado. Isso preserva os dados do visitante entre as atualizações de SDK. Para novas instalações do SDK 4.x, o identificador do usuário é `null` até que seja definido.

   * Esta é a sintaxe para este método:

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * Esta é a amostra de código para este método:

      ```csharp
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

      ```javascript
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

      ```javascript
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging();
      ```

* **SetDebugLogging (winJS: setDebugLogging)**

   Define a preferência do log de depuração como `debugLogging`. O registro em log de depuração funciona somente ao usar a versão de depuração da biblioteca, a versão de lançamento ignora essa configuração.

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

   Indica ao SDK que os dados do ciclo de vida devem ser coletados para uso em todas as soluções no SDK. Para obter mais informações, consulte [Medições de ciclo de vida](/help/universal-windows/metrics.md).

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

   Indica ao SDK que o aplicativo está pausado, a fim de calcular corretamente as medições de ciclo de vida. Por exemplo, ao pausar coleta um carimbo de data e hora para determinar a duração da sessão anterior. Isso também define um sinalizador para que o ciclo de vida saiba corretamente que o aplicativo não falhou. Para obter mais informações, consulte [Medições de ciclo de vida](/help/universal-windows/metrics.md).

   * Esta é a sintaxe para este método:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
