---
description: Classes e métodos fornecidos pela biblioteca da plataforma Universal Windows.
seo-description: Classes e métodos fornecidos pela biblioteca da plataforma Universal Windows.
seo-title: Métodos do SDK
solution: Marketing Cloud, Analytics
title: Métodos do SDK
topic: Desenvolvedor e implementação
uuid: e 3 aa 41 d 6-7 bc 0-4208-a 662-12907 c 209 a 77
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

Classes e métodos fornecidos pela biblioteca da plataforma Universal Windows.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **Getversion (winjs: Getversion)**

   Retorna a versão atual da biblioteca do Adobe Mobile.

   * Esta é a sintaxe para este método:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **Getprivacystatusasync (winjs: Getprivacystatusasync)**

   Retorna a representação de enumeração do status de privacidade do usuário atual.

   * `ADBMobilePrivacyStatusOptIn` - As ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut` - As ocorrências são descartadas.
   * `ADBMobilePrivacyStatusUnknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

      The default value is set in the `ADBMobileConfig.json` config file. Para obter mais informações, consulte [Arquivo de configuração adbmobileconfig. json](/help/universal-windows/c-configuration/c.json.md).

   * Esta é a sintaxe para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * Aqui estão exemplos de código para este método:

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

* **Setprivacystatus (winjs: Setprivacystatus)**

   Define o de privacidade do usuário atual como `status`status. É definido como um dos valores abaixo:
   * `ADBMobilePrivacyStatusOptIn` - as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut` - as ocorrências serão descartadas.
   * `DBMobilePrivacyStatusUnknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas. Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

      * Esta é a sintaxe para este método:

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * Aqui estão exemplos de código para este método:

         **C-sharp**

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

* **Getlifetimevalue (winjs: Getlifetimevalue)**

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

* **Getuseridentifier (winjs: Getuseridentifier)**

   Retorna o identificador do usuário personalizado se algum estiver configurado. Returns `null` if a custom identifier is not set.
O valor padrão é `null`.

   >[!IMPORTANT]
   >
   >Se o aplicativo for atualizado do SDK 3. x da Experience Cloud para o 4. x, o serviço de ID anterior (personalizado ou gerado automaticamente) será recuperado e armazenado como o identificador do usuário personalizado. Isso preserva os dados do visitante entre as atualizações de SDK. Para novas instalações do SDK 4.x, o identificador do usuário é `null` até que seja definido.

   * Esta é a sintaxe para este método:

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * Esta é a amostra de código para este método:

      ```csharp
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **Setuseridentifier (winjs: Setuseridentifier)**

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

* **Getdebuglogging (winjs: Getdebuglogging)**

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

* **Setdebuglogging (winjs: Setdebuglogging)**

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

* **Collectlifecycledata (winjs: Collectlifecycledata)**

   Indica ao SDK que os dados do ciclo de vida devem ser coletados para uso em todas as soluções no SDK. Para obter mais informações, consulte  [Medições de ciclo de vida](/help/universal-windows/metrics.md).

   * Esta é a sintaxe para este método:

      ```csharp
      static void CollectLifecycleData();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData();
      ```

* **Pausecollectinglifecycledata (winjs: Pausecollectinglifecycledata)**

   Indica ao SDK que o aplicativo está pausado, a fim de calcular corretamente as métricas de ciclo de vida. Por exemplo, durante a pausa um carimbo de data e hora é coletado para determinar a duração da sessão anterior. Também define um sinalizador para que o ciclo de vida saiba que o aplicativo não parou de funcionar. Para obter mais informações, consulte [Medições de ciclo de vida](/help/universal-windows/metrics.md).

   * Esta é a sintaxe para este método:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
