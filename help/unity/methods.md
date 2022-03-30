---
description: ADBMobile.cs configuration methods
keywords: Unity
solution: Experience Cloud Services
title: Métodos do ADBMobile.css
uuid: af504934-febd-45d9-81e2-2a310f4c65dc
exl-id: d12c16f1-c25c-4698-8943-a660d9c08faf
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 70%

---

# Métodos do ADBMobile.css {#adbmobile-cs-methods}

## Métodos de configuração

* **CollectLifecycleData**

   Indica ao SDK que os dados do ciclo de vida devem ser coletados para uso em todas as soluções no SDK. Para obter mais informações, consulte [Medições de ciclo de vida](/help/ios/metrics.md).

   * Esta é a sintaxe para este método:

      ```java
      public static void CollectLifecycleData();
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.CollectLifecycleData();
      ```

* **EnableLocalNotifications (iOS only)**

   Ative as notificações locais no aplicativo.

   * Esta é a sintaxe para este método:

      ```java
      public static void EnableLocalNotifications();
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.EnableLocalNotifications();
      ```

* **GetDebugLogging**

   Retorna a preferência de log para a depuração atual. O valor padrão é `false`.

   * Esta é a sintaxe para este método:

      ```java
      public static bool GetDebugLogging();
      ```

   * Esta é a amostra de código para este método:

      ```java
      var debugEnabled = ADBMobile.GetDebugLogging();
      ```

* **GetLifetimeValue**

   Retorna o valor do tempo de vida do usuário atual.

   * Esta é a sintaxe para este método:

      ```java
      public static double GetLifetimeValue();
      ```

   * Esta é a amostra de código para este método:

      ```java
      var lifetimeValuea = ADBMobile.GetLifetimeValue();
      ```

* **GetPrivacyStatus**

   Retorna a representação de enumeração do status de privacidade do usuário atual.
   * `MOBILE_PRIVACY_STATUS_OPT_IN`: as ocorrências são enviadas imediatamente.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: as ocorrências são descartadas.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: se o rastreamento offline estiver ativado, as ocorrências são salvas até o status de privacidade ser alterado para aceitar (e então as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas).

      Se o rastreamento offline não estiver ativado, as ocorrências são descartadas até o status de privacidade ser alterado parar aceitar. O valor padrão é definido na variável [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md) arquivo.

   * Esta é a sintaxe para este método:

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * Esta é a amostra de código para este método:

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **GetUserIdentifier**

   Returns the custom user identifier if a custom identifier has been set. Retorna null se um identificador personalizado não estiver configurado. O valor padrão é `null`.

   * Esta é a sintaxe para este método:

      ```java
      public static string GetUserIdentifier();
      ```

   * Esta é a amostra de código para este método:

      ```java
      var userId = ADBMobile.GetUserIdentifier();
      ```

* **GetVersion**

   Obtém a versão da biblioteca.

   * Esta é a sintaxe para este método:

      ```java
      public static string GetVersion();
      ```

   * Esta é a amostra de código para este método:

      ```java
      var version = ADBMobile.GetVersion();
      ```

* **KeepLifecycleSessionAlive (somente iOS)**

   Indica ao SDK que o próximo resumo em segundo plano não deve iniciar uma nova sessão, independentemente do tempo limite de valor da sessão do ciclo de vida presente no arquivo de configuração.

   >[!TIP]
   >
   >Este método é destinado a aplicativos que realizam registros para receber notificações enquanto são executados em segundo plano e só deve ser chamado a partir do código executado enquanto o aplicativo está funcionando em segundo plano.

   * Esta é a sintaxe para este método:

      ```java
      public static void KeepLifecycleSessionAlive();
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.KeepLifecycleSessionAlive();
      ```

* **PauseCollectingLifecycleData (somente Android)**

   Indica ao SDK que o aplicativo está pausado, a fim de calcular corretamente as medições de ciclo de vida. Por exemplo, ao pausar, um carimbo de data e hora é coletado para determinar a duração da sessão anterior. This also sets a flag so that lifecycle correctly knows that the app did not crash. Para obter mais informações, consulte [Medições de ciclo de vida](/help/android/metrics.md).

   * Esta é a sintaxe para este método:

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.PauseCollectingLifecycleData();
      ```

* **SetContext (somente Android)**

   Indicates to the SDK that it should set its application context from the UnityPlayer&#39;s current activity.

   * Esta é a sintaxe para este método:

      ```java
      public static void SetContext();
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.SetContext();
      ```

* **SetDebugLogging**

   Define a preferência do log de depuração como ativada.

   * Esta é a sintaxe para este método:

      ```java
      public static void SetDebugLogging (bool enabled);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.SetDebugLogging(true);
      ```

* **SetPrivacyStatus**

   Sets the privacy status for the current user to status. É definido como um dos valores abaixo:

   * `MOBILE_PRIVACY_STATUS_OPT_IN`: as ocorrências são enviadas imediatamente.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: as ocorrências são descartadas.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: se o rastreamento offline estiver ativado, as ocorrências são salvas até o status de privacidade ser alterado para aceitar (e então as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o rastreamento offline não estiver ativado, as ocorrências são descartadas até o status de privacidade ser alterado parar aceitar.

   * Esta é a sintaxe para este método:

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus);
      ```

   * Here is the code sample for this syntax:

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   Define o identificador do usuário para userId.

   * Esta é a sintaxe para este método:

      ```java
      public static void SetUserIdentifier(string userId);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.SetUserIdentifier("myCustomUserId");
      ```

## Métodos do Analytics

* **GetTrackingIdentifier**

   Recupera o identificador do rastreamento de análises.

   * Esta é a sintaxe para este método:

      ```java
      public static string GetTrackingIdentifier();
      ```

   * Esta é a amostra de código para este método:

      ```java
      var trackingId = ADBMobile.GetTrackingIdentifier();
      ```

* **TrackState**

   Rastreia um estado de aplicativo com dados de contexto opcionais. Os estados são as exibições disponíveis no aplicativo, como &quot;tela inicial&quot;, &quot;nível 1&quot;, &quot;pausa&quot; e assim por diante. Esses estados são semelhantes às páginas em um site, e as chamadas de `TrackState` aumentam as visualizações de página.

   Se o estado estiver vazio, será exibido como *`app name app version (build)`* em relatórios. Caso veja esse valor em relatórios, certifique-se de configurar um estado em cada `TrackState` chame.

   >[!TIP]
   >
   >Esta é a única chamada de rastreamento que aumenta as exibições de página.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackState(string state, Dictionary<string, object> cdata);
      ```

   * Esta é a amostra de código para este método:

      ```java
      var contextData = new Dictionary<string, object>);
      contextData.Add ("user", "jim");
      ADBMobile.TrackState("title screen", contextData);
      ```

* **TrackAction**

   Rastreia uma ação no seu aplicativo. As ações são coisas que ocorrem no seu aplicativo e que deseja medir, como &quot;mortes&quot;, &quot;nível obtido&quot;, &quot;assinaturas de feed&quot; e outras métricas.

   >[!TIP]
   >
   >Se você tem um código que pode funcionar enquanto o aplicativo é executado em segundo plano (por exemplo, uma recuperação de dados em segundo plano), use `trackActionFromBackground`.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackAction(string action, Dictionary<string, object> cdata);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.TrackAction("level gained", null);
      ```

* **TrackActionFromBackground (somente iOS)**

   Rastreia uma ação que ocorreu em segundo plano. Impede que os eventos do ciclo de vida sejam acionados em determinados cenários.

   >[!TIP]
   >
   >Este método deve ser chamado somente no código em execução enquanto o aplicativo estiver em segundo plano.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackActionFromBackground(string action, Dictionary<string,object> cdata);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Envia as coordenadas atuais de latitude e longitude. Também usa pontos de interesse definidos no arquivo `ADBMobileConfig.json` a fim de determinar se o local fornecido como parâmetro está dentro do POI. Se as coordenadas atuais estão dentro de um POI definido, uma variável de dados de contexto é preenchida e enviada com a chamada TrackLocation .

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackLocation(float latValue, float lonValue, Dictionary<string, object> cdata);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.TrackLocation(28.418649, -81.581324, null);
      ```

* **TrackBeacon**

   Rastreia quando um usuário está perto de um beacon.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackBeacon(int major, int minor, string uuid, ADBBeaconProximity proximity, Dictionary<string, object> cdata);
      ```

* **TrackingClearCurrentBeacon**

   Apaga os dados de beacons depois que o usuário se distancia de um.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   Adiciona uma quantia ao valor do ciclo de vida do usuário.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackLifetimeValueIncrease(double amount, Dictionary<string, object> cdata);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.TrackLifetimeValueIncrease(5, null);
      ```

* **TrackTimedActionStart**

   Inicia uma ação programada com a ação de nome. Se você chamar este método para uma ação já iniciada, a ação programada anterior será substituída.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackTimedActionStart(string action, Dictionary<string,object> cdata);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Pass in data to update the context data associated with the given action. Os dados transmitidos são anexados aos existentes para a ação em questão e os substituem se a mesma chave já estiver definida para a ação.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackTimedActionUpdate(string action, Dictionary<string, object> cdata);
      ```

   * Esta é a amostra de código para este método:

      ```java
      var contextData = new Dictionary<string, object>;
      contextData.Add("checkpoint", "1:32");
         ADBMobile.TrackTimedActionUpdate("level2", contextData);
      ```

* **TrackTimedActionEnd**

   Encerra uma ação programada.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackTimedActionEnd(string action);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.TrackTimedActionEnd("level2");
      ```

* **TrackingTimedActionExists**

   Retorna se uma ação programada está em andamento ou não.

   * Esta é a sintaxe para este método:

      ```java
      public static bool TrackingTimedActionExists(string action);
      ```

   * Esta é a amostra de código para este método:

      ```java
       var level2InProgress = ADBMobile.TrackingTimedActionExists("level2");
      ```

* **TrackingSendQueuedHits**

   Força a biblioteca a enviar todas as ocorrências na fila offline, independentemente de quantas estão na fila no momento.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackingSendQueuedHits();
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.TrackingSendQueuedHits();
      ```

* **TrackingClearQueue**

   Apaga todas as ocorrências da fila offline.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackingClearQueue();
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   Recupera o número de ocorrências na fila offline.

   * Esta é a sintaxe para este método:

      ```java
      public static int TrackingGetQueueSize();
      ```

   * Esta é a amostra de código para este método:

      ```java
      var queueSize = ADBMobile.TrackingGetQueueSize();
      ```

## Métodos de ID do Experience Cloud

* **GetMarketingCloudID**

   Recupera a Experience Cloud ID a partir do serviço de ID.

   * Esta é a sintaxe para este método:

      ```java
      public static string GetMarketingCloudID();
      ```

   * Esta é a amostra de código para este método:

      ```java
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Com a ID do Experience Cloud, é possível definir outras IDs do cliente para associar a cada visitante. The Visitor API accepts multiple Customer IDs for the same visitor, along with a customer type identifier to separate the scope of the different customer IDs. Este método corresponde a setCustomerIDs na biblioteca do JavaScript.

   * Esta é a sintaxe para este método:

      ```java
      public static void VisitorSyncIdentifiers(Dictionary<string, object> identifiers);
      ```

   * Esta é a amostra de código para este método:

      ```java
      var ids = new Dictionary<string, object> ();
      ids.Add ("player1", "jimbob");
      ADBMobile.VisitorSyncIdentifiers(ids);
      ```

## Métodos de aquisição 

* **ProcessGooglePlayInstallReferrerUrl** *(Somente Android)*

   Passe o URL do referenciador retornado de uma chamada para a API do Referenciador de instalação do Google Play para este método.

   * Esta é a sintaxe para este método:

      ```java
      public static void ProcessGooglePlayInstallReferrerUrl(string referrerUrl);
      ```

   * Esta é a amostra de código para este método:

      ```java
      // in actual implementation, the referrer url should be retrieved
      // from the Google Play Install Referrer API.
      var myReferrer = "utm_source=unityTestSource&utm_content=unityTestContent&utm_campaign=unityTestCampaign";
      ADBMobile.ProcessGooglePlayInstallReferrerUrl(myReferrer);
      ```
