---
description: Classes e métodos fornecidos pela biblioteca Universal App Store do Windows 8.1.
solution: Experience Cloud Services,Analytics
title: Métodos do SDK
topic-fix: Developer and implementation
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2cea
exl-id: c328fd79-6e10-43b7-9d08-8da395098b60
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 51%

---

# Métodos do SDK {#sdk-methods}

Classes e métodos fornecidos pela biblioteca Universal App Store do Windows 8.1.

>[!TIP]
>
>Ao consumir `winmd` métodos do winJS (JavaScript), todos os métodos passam a ter a primeira letra em minúsculas automaticamente.

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
   * `ADBMobilePrivacyStatusUnknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (e então as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

      O valor padrão é definido na variável [Configuração do ADBMobileConfig.json](/help/windows-appstore/c-configuration/c.json.md) arquivo.

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
   * `ADBMobilePrivacyStatusUnknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (e então as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

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

   Retorna o identificador do usuário personalizado se algum identificador personalizado estiver configurado. Retorna null se um identificador personalizado não estiver configurado. O valor padrão é `null`.

   >[!TIP]
   >
   >Se seu aplicativo for atualizado do SDK 3.x do Experience Cloud para o 4.x, a ID anterior (personalizada ou gerada automaticamente) será recuperada e armazenada como o identificador de usuário personalizado. Isso preserva os dados do visitante entre as atualizações de SDK. Para novas instalações no SDK 4.x, o identificador do usuário é `null` até ser definido.

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

   Define a preferência do log de depuração como `debugLogging`. O log de depuração funciona somente ao usar a versão de depuração da biblioteca, a versão de lançamento ignora essa configuração.

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
   >Chame esse método no `onResume()` em cada Atividade dentro do aplicativo, como mostrado no exemplo a seguir. Também recomendamos transmitir a Atividade ou o Serviço como o objeto de contexto em vez do contexto de Aplicativo global.

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

   Indica ao SDK que o aplicativo está pausado, a fim de calcular corretamente as medições de ciclo de vida. Por exemplo, ao pausar, um carimbo de data e hora é coletado para determinar a duração da sessão anterior. Isso também define um sinalizador para que o ciclo de vida saiba que o aplicativo não parou de funcionar. Para obter mais informações, consulte [Medições de ciclo de vida](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Chame esse método no `onPause()` métodos em cada atividade dentro do aplicativo, como mostrado no exemplo . Também recomendamos transmitir a Atividade ou o Serviço como o objeto de contexto em vez do contexto de Aplicativo global.

   * Esta é a sintaxe para este método:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
