---
description: Classes e métodos fornecidos pela biblioteca da loja de aplicativos universal do Windows 8.1.
seo-description: Classes e métodos fornecidos pela biblioteca da loja de aplicativos universal do Windows 8.1.
seo-title: Métodos do SDK
solution: Experience Cloud,Analytics
title: Métodos do SDK
topic: Developer and implementation
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2cea
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 50%

---


# Métodos do SDK {#sdk-methods}

Classes e métodos fornecidos pela biblioteca da loja de aplicativos universal do Windows 8.1.

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
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **GetPrivacyStatusAsync (winJS: getPrivacyStatusAsync)**

   Retorna a representação de enumeração do status de privacidade do usuário atual.

   * `ADBMobilePrivacyStatusOptIn` - as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut` - as ocorrências serão descartadas.
   * `ADBMobilePrivacyStatusUnknown` - Se o conjunto de relatórios tiver um carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

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

   Define o de privacidade do usuário atual como `status` status. É definido como um dos valores abaixo:

   * `ADBMobilePrivacyStatusOptIn` - as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut` - as ocorrências serão descartadas.
   * `ADBMobilePrivacyStatusUnknown` - Se o conjunto de relatórios tiver um carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

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

   Retorna o identificador de usuário personalizado se um identificador personalizado tiver sido definido. Retorna null se um identificador personalizado não estiver definido. O valor padrão é `null`.

   >[!TIP]
   >
   >Se seu aplicativo for atualizado do SDK Experience Cloud 3.x para 4.x, a ID anterior (personalizada ou gerada automaticamente) será recuperada e armazenada como o identificador de usuário personalizado. Isso preserva os dados do visitante entre as atualizações de SDK. For new installations on the 4.x SDK, user identifier is `null` until set.

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

   Indica ao SDK que os dados do ciclo de vida devem ser coletados para uso em todas as soluções no SDK. Para obter mais informações, consulte [Medições de ciclo de vida](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Chame esse método no `onResume()` método de cada Atividade dentro do aplicativo, como mostrado no exemplo a seguir. Também recomendamos transmitir a Atividade ou o Serviço como o objeto de contexto em vez do contexto global do Aplicativo.

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

   Indica ao SDK que o aplicativo está pausado, a fim de calcular corretamente as medições de ciclo de vida. Por exemplo, ao pausar coleta um carimbo de data e hora para determinar a duração da sessão anterior. Isso também define um sinalizador para que o ciclo de vida saiba corretamente que o aplicativo não falhou. Para obter mais informações, consulte [Medições de ciclo de vida](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Chame esse método nos `onPause()` métodos de cada Atividade dentro do seu aplicativo, como mostrado no exemplo. Também recomendamos transmitir a Atividade ou o Serviço como o objeto de contexto em vez do contexto global do Aplicativo.

   * Esta é a sintaxe para este método:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
