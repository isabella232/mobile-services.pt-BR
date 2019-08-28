---
description: Métodos do Android para componentes do Xamarin para os SDK 4.x das soluções da Experience Cloud.
keywords: Xamarin
seo-description: Métodos do Android para componentes do Xamarin para os SDK 4.x das soluções da Experience Cloud.
seo-title: Métodos do Android
solution: Marketing Cloud, desenvolvedor
title: Métodos do Android
uuid: 860 af 1 c 4-f 57 e -4 bcb -8308-4 e 316 da 9 a 27 b
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Android methods{#android-methods}

Métodos do Android para componentes do Xamarin para os SDK 4.x das soluções da Experience Cloud.

## Configuration methods {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **Debuglogging**

   Retorna a preferência de log de depuração atual e o padrão é false.

   * Esta é a sintaxe para este método:

      ```java
      public static Boolean DebugLogging;
      ```

   * Esta é a amostra de código para este método:

      ```java
      getter: var debuglog = Config.DebugLogging;
      setter: Config.DebugLogging = (Java.Lang.Boolean)true;
      ```

* **LifetimeValue**

   Retorna o valor do tempo de vida do usuário atual.

   * Esta é a sintaxe para este método:

      ```java
      public static BigDecimal LifetimeValue; 
      ```

   * Esta é a amostra de código para este método:

      ```java
       var lifetimeValue = Config.LifetimeValue;
      ```

* **PrivacyStatus**

   Retorna a representação de enumeração do status de privacidade do usuário atual.
   * `ADBMobilePrivacyStatus.OptIn` - as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatus.OptOut` - as ocorrências serão descartadas.
   * `ADBMobilePrivacyStatus.Unknown` - se o rastreamento offline estiver ativado, as ocorrências são salvas até o status de privacidade ser alterado para aceitar (e então as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o rastreamento offline não estiver ativado, as ocorrências são descartadas até o status de privacidade ser alterado parar aceitar.
   O valor padrão está definido no arquivo [ADBMobileConfig.json](/help/android/configuration/json-config/json-config.md).

   * Esta é a sintaxe para este método:

      ```java
      public static MobilePrivacyStatus PrivacyStatus; 
      ```

   * Esta é a amostra de código para este método:

      ```java
      getter: var privacyStatus = Config.PrivacyStatus; 
      setter: Config.PrivacyStatus = MobilePrivacyStatus.MobilePrivacyStatusUnknown;
      ```


* **UserIdentifier**

   Se um identificador personalizado tiver sido definido, retorne esse identificador. Se um identificador personalizado não estiver definido, retorna null. O valor padrão é `null`.

   * Esta é a sintaxe para este método:

      ```java
      public static UserIdentifier();
      ```

   * Esta é a amostra de código para este método:

      ```java
      getter: var userId = Config.UserIdentifier;
      setter: Config.UserIdentifier = "imBatman";
      ```

* **Versão**

   Obtém a versão da biblioteca.

   * Esta é a sintaxe para este método:

      ```java
      public static string Version;
      ```

   * Esta é a amostra de código para este método:

      ```java
      var version = ADBMobile.Version;
      ```

* **PauseCollectingLifecycleData**

   Indica ao SDK que o aplicativo está pausado, a fim de calcular corretamente as métricas de ciclo de vida. Por exemplo, durante a pausa um carimbo de data e hora é coletado para determinar a duração da sessão anterior. Também define um sinalizador para que o ciclo de vida saiba que o aplicativo não parou de funcionar. Para obter mais informações, consulte [Medições de ciclo de vida](/help/android/metrics.md).

   * Esta é a sintaxe para este método:

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData (atividade Activity)**

   (4.2 ou superior) Indica ao SDK que os dados do ciclo de vida devem ser coletados para uso em todas as soluções no SDK. Para obter mais informações, consulte [Medições de ciclo de vida](/help/android/metrics.md).

   * Esta é a sintaxe para este método:

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData (atividade Activity)**

   (4.2 ou superior) Indica ao SDK que os dados do ciclo de vida devem ser coletados para uso em todas as soluções no SDK. Para obter mais informações, consulte [Medições de ciclo de vida](/help/android/metrics.md).

   * Esta é a sintaxe para este método:

      ```java
      public static void collectLifecycleData(Activity activity, IDictionary<string, Object> context));
      ```

   * Esta é a amostra de código para este método:

      ```java
      IDictionary<string, Java.Lang.Object> context = new Dictionary<string, 
      Java.Lang.Object> ();
      context.Add ("key", "value");
      Config.CollectLifecycleData (this, context);
      ```

* **OverrideConfigStream**

   (4.2 or later) Lets you load a different `ADBMobile JSON` config file when the application starts. A configuração diferente é utilizada até o aplicativo ser fechado.

   * Esta é a sintaxe para este método:

      ```java
      public static void OverrideConfigStream (Stream stream);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Stream st1 = Assets.Open ("ADBMobileConfig-2.json"); 
      Config.OverrideConfigStream (st1); 
      ```

* **SetLargeIconResourceId(int resourceId)**

   (4.2 ou superior) Define o ícone grande usado para notificações criadas pelo SDK. Este ícone é a principal imagem exibida quando o usuário visualiza a notificação completa na central de notificações.

   * Esta é a sintaxe para este método:

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   (4.2 ou superior) Define o ícone pequeno usado para notificações criadas pelo SDK. Esse ícone é exibido na barra de status e é a imagem secundária exibida quando o usuário visualiza a notificação completa na central de notificações.

   * Esta é a sintaxe para este método:

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * Esta é a amostra de código para este método:

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Analytics methods {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Retorna a ID gerada automaticamente pelo Analytics. Esta é uma ID única e específica do aplicativo que é gerada na primeira inicialização e é armazenada e utilizada a partir desse ponto. Essa ID é preservada entre as atualizações do aplicativo e é removida na desinstalação.

   * Esta é a sintaxe para este método:

      ```java
      public static string TrackingIdentifier;
      ```

   * Esta é a amostra de código para este método:

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   Rastreia um estado de aplicativo com dados de contexto opcionais. `States` são as exibições disponíveis no aplicativo, como "tela inicial", "nível 1", "pausa" e assim por diante. Esses estados são semelhantes às páginas em um site e as chamadas de `TrackState` aumentam as exibições de página. Se o estado está vazio, então é exibido como "nome do aplicativo e versão do aplicativo (construção)" nos relatórios. Se você encontrar esse valor nos relatórios, certifique-se de que esteja definindo state em cada chamada de `TrackState`.

   >[!TIP]
   >
   >Esta é a única chamada de rastreamento que aumenta as exibições de página.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackState (string state, IDictionary<string, Object> cdata); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object>(); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackState ("stateName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackAction**

   Rastreia uma ação no seu aplicativo. As ações são coisas que ocorrem no aplicativo e que você deseja medir, como "mortes", "nível obtido", "assinaturas de feed" e outras métricas.

   >[!TIP]
   >
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackAction(string action, IDictionary<string,Object> cdata); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value");
      Analytics.TrackAction ("actionName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackLocation**

   Envia as coordenadas atuais de latitude e longitude. Also uses points of interest defined in the `ADBMobileConfig.json` file to determine whether the location that was provided as a parameter is in any of your POIs. Se as coordenadas atuais estão dentro de um POI definido, uma variável de dados de contexto é preenchida e enviada com a chamada `TrackLocation`.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackLocation(Location location, IDictionary<string, Object> cdata); 
      ```

   * Esta é a amostra de código para este método:

      ```java
       Location loc = new Location(LocationManager.GpsProvider);;
       loc.Latitude = 111; 
       loc.Longitude = 44; 
       loc.Accuracy = 5; 
       Analytics.TrackLocation (loc, null);
      ```

* **TrackBeacon**

   Rastreia quando um usuário está perto de um beacon.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackBeacon (string uuid, string major, string minor,  Analytics.BEACON_PROXIMITY prox, IDictionary<string, Object> cdata); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.TrackBeacon ("UUID", "1", "2", 
      Analytics.BEACON_PROXIMITY.ProximityImmediate, null); 
      ```

* **ClearBeacon**

   Apaga os dados de beacons depois que o usuário se distancia de um.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.ClearBeacon(); 
      ```

* **TrackLifetimeValueIncrease**

   Adiciona uma quantia ao valor do ciclo de vida do usuário.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackLifetimeValueIncrease (double amount, IDictionary<string,Object> cdata); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.TrackLifetimeValueIncrease(5,null);
      ```

* **TrackTimedActionStart**

   Inicia uma ação programada com a ação de nome. Se você chamar este método para uma ação já iniciada, a ação programada anterior será substituída.

   >[!TIP]
   >
   > Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackTimedActionStart(string action,IDictionary<string, Object> cdata); 
      ```

   * Esta é uma amostra de código para este método:

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Repassa os dados para atualizar os dados de contexto associados à ação. Os dados transmitidos são anexados aos atuais para a ação em questão, e substituem os dados se a mesma chave já estiver definida para a ação.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackTimedActionUpdate(string action, IDictionary<string, Object> cdata); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      var updatedData = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   Encerra uma ação programada.

   * Esta é a sintaxe para este método:

      ```java
      public static void TrackTimedActionEnd(string action,
        Analytics.ITimedActionBlock block);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.TrackTimedActionEnd ("level2", new TimedActionBlock()); 
           class TimedActionBlock: Java.Lang.Object, 
      Analytics.ITimedActionBlock{ 
           public Java.Lang.Object Call (long inAppDuration, long 
      totalDuration IDictionary<string, Java.Lang.Object> contextData){ 
           return Java.Lang.Boolean.True; 
        } 
      }
      ```

* **TrackingTimedActionExists**

   Retorna se uma ação cronometrada estiver em andamento.

   * Esta é a sintaxe para este método:

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      var level2InProgress = Analytics.TrackingTimedActionExists("level2"); 
      ```

* **SendQueuedHits**

   Força a biblioteca a enviar todas as ocorrências na fila offline, independentemente de quantas ocorrências estão na fila no momento.

   * Esta é a sintaxe para este método:

      ```java
      public static void SendQueuedHits();
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.SendQueuedHits(); 
      ```

* **ClearQueue**

   Apaga todas as ocorrências da fila offline.

   * Esta é a sintaxe para este método:

      ```java
      public static void ClearQueue(); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Analytics.ClearQueue(); 
      ```

* **QueueSize**

   Recupera o número de ocorrências que estão atualmente na fila offline.

   * Esta é a sintaxe para este método:

      ```java
      public static long QueueSize(); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      var queueSize = Analytics.QueueSize();
      ```

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

* **MarketingCloudId**

   Recupera a Experience Cloud ID a partir do serviço de ID.

   * Esta é a sintaxe para este método:

      ```java
      public static string MarketingCloudId;
      ```

   * Esta é a amostra de código para este método:

      ```java
      var mcid = Visitor.MarketingCloudId;
      ```

* **SyncIdentifiers**

   Com a Experience Cloud ID, é possível definir outras IDs do cliente para associar com cada visitante. A API de visitante aceita várias IDs do cliente para o mesmo visitante, junto com um identificador de tipo de cliente para separar o escopo de diferentes IDs do cliente. Este método corresponde a `setCustomerIDs` na biblioteca do JavaScript.

   * Esta é a sintaxe para este método:

      ```java
      public static void SyncIdentifiers((IDictionary<string> identifiers);
      ```

   * Esta é a amostra de código para este método:

      ```java
      IDictionary<string,string> ids = new Dictionary<string, string> ();
      ids.Add ("pushID", ;"value2");
      Visitor.SyncIdentifiers (ids);
      ```

## Métodos do Target {#section_C1E4121CAF9D43538511D857A1F549A7}

* **LoadRequest**

   Sends a request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

   * Esta é a sintaxe para este método:

      ```java
      public static void LoadRequest (TargetLocationRequest request, Target.ITargetCallback callback); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      class TargetBlock: Java.Lang.Object, Target.ITargetCallback{ 
          public void Call (Java.Lang.Object content) 
         { 
          Console.WriteLine (content.ToString()); 
         } 
      } 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
           Target.LoadRequest (req, new TargetBlock()); 
      ```

* **CreateRequest**

   O construtor de conveniência cria um objeto `ADBTargetLocationRequest` com os parâmetros em questão.

   * Esta é a sintaxe para este método:

      ```java
      public static TargetLocationRequest TargetCreateRequest(string name,string defaultContent,IDictionary<string,string> parameters); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      IDictionary<string, Java.Lang.Object> parameters = new Dictionary> string, Java.Lang.Object> (); 
          parameters.Add ("key1", "value2"); 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
      ```

* **CreateOrderConfirmRequest**

   Cria um `ADBTargetLocationRequest`.

   * Esta é a sintaxe para este método:

      ```java
      public static TargetLocationRequest TargetCreateRequest (string name, string defaultContent, IDictionary<;string, string> parameters);
      ```

   * Esta é a amostra de código para este método:

      ```java
      var orderConfirm = Target.CreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **ClearCookies**

   Limpa os cookies do Target do seu aplicativo.

   * Esta é a sintaxe para este método:

      ```java
      public static void ClearCookies(); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Target.ClearCookies (); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **VisitorProfile**

   Retorna o perfil do visitante obtido recentemente. Retorna nulo se nenhum sinal foi enviado ainda. O perfil do visitante é salvo em `NSUserDefaults` para facilitar o acesso nas várias inicializações do aplicativo.

   * Esta é a sintaxe para este método:

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * Esta é a amostra de código para este método:

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   Returns the current `DPID`.

   * Esta é a sintaxe para este método:

      ```java
      public static string Dpuuid; 
      ```

   * Esta é a amostra de código para este método:

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **Dpuuid**

   Returns the current `DPUUID`.

   * Esta é a sintaxe para este método:

      ```java
      public static string AudienceDpuuid; 
      ```

   * Esta é a amostra de código para este método:

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **AudienceSetDpidAndDpuuid**

   Define o `dpid` e `dpuuid`. If `dpid` and `dpuuid` are set, they are sent with each signal.

   * Esta é a sintaxe para este método:

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * Esta é a amostra de código para este método:

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **SignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>` callback.

   * Esta é a sintaxe para este método:

      ```java
      public static void SignalWithData (IDictionary<string, Object> audienceData, AudienceManager.IAudienceManagerCallback callback); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      class AudienceManagerCallback: Java.Lang.Object, 
       AudienceManager.IAudienceManagerCallback{ 
         public void Call (Java.Lang.Object content) 
        {
          Console.WriteLine (content.ToString()); 
        }
      }
      IDictionary<string, Java.Lang.Object> traits = new Dictionary<string, 
      Java.Lang.Object> (); 
         traits.Add ("trait", "b");
      AudienceManager.SignalWithData (traits, new AudienceManagerCallback());
      ```

* **Redefinir**

   Redefine a `UUID` do gerenciador de público-alvo e limpa o perfil de visitante atual.

   * Esta é a sintaxe para este método:

      ```java
      public static void Reset ();
      ```

   * Esta é a amostra de código para este método:

      ```java
       AudienceManager.Reset ();
      ```

## Vídeo {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Para obter mais informações sobre a Análise de vídeo, consulte [Análise de vídeo](/help/android/analytics-main/video-qs.md).

* **MediaSettings**

   Retorna um objeto `MediaSettings` com parâmetros especificados.

   * Esta é a sintaxe para este método:

      ```java
      public static MediaSettings SettingsWith (string name, double length, string playerName, string playerID);  
      ```

   * Esta é a amostra de código para este método:

      ```java
      MediaSettings settings = Media.SettingsWith("name1", 10, "playerName1", "playerID1");
      ```

* **AdSettingsWith**

   Retorna um objeto `MediaSettings` a ser utilizado no rastreamento de um vídeo de anúncio.

   * Esta é a sintaxe para este método:

      ```java
      public static MediaSettings AdSettingsWith ( string name, double length, 
        string playerName, string parentName, string parentPod, 
      double parentPodPosition, string CPM); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      MediaSettings adSettings = Media.AdSettingsWith ("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1"); 
      ```

* **Abrir**

   Abre um objeto `ADBMediaSettings` para rastreamento.

   * Esta é a sintaxe para este método:

      ```java
      public static void Open (MediaSettings settings, Media.IMediaCallback callback);
      ```

   * Esta é a amostra de código para este método:

      ```java
      MediaSettings settings = Media.SettingsWith ("name1", 10, "playerName1", "playerID1"); 
         Media.Open (settings, new MediaCallback()); 
         class MediaCallback: Java.Lang.Object, Media.IMediaCallback{ 
      public void Call (Java.Lang.Object content) 
      {
      }
      }
      ```

* **Close**

   Fecha o item de mídia com nome.

   * Esta é a sintaxe para este método:

      ```java
      public static void Close(string name);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.Close (settings.Name); 
      ```

* **Reproduzir**

   Reproduz o item de mídia com o nome no deslocamento em questão (em segundos).

   * Esta é a sintaxe para este método:

      ```java
      public static void Play ( string name, double offset); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **Concluído**

   Marca manualmente o item de mídia como concluído no deslocamento em questão (em segundos).

   * Esta é a sintaxe para este método:

      ```java
      public static void Complete (string name, double offset); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **Stop**

   Notifica ao módulo de mídia que o vídeo foi interrompido ou pausado no deslocamento em questão.

   * Esta é a sintaxe para este método:

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **Clique em**

   Notifica ao módulo de mídia que o item de mídia foi clicado.

   * Esta é a sintaxe para este método:

      ```java
      public static void Click ( string name, double offset); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **Caminho**

   Envia uma chamada de ação de rastreamento (sem exibição de página) para o estado de mídia atual.

   * Esta é a sintaxe para este método:

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.Track (settings.Name, null); 
      ```
