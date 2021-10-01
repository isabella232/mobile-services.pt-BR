---
description: Métodos do Android para componentes do Xamarin para o SDK 4.x das soluções do Experience Cloud.
keywords: Xamarin
solution: Experience Cloud
title: Métodos do Android
uuid: 860af1c4-f57e-4bcb-8308-4e316da9a27b
exl-id: 0de1fa11-37e9-49be-8d42-a13cb4a3f0e3
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '1755'
ht-degree: 68%

---

# Métodos do Android{#android-methods}

Métodos do Android para componentes do Xamarin para o SDK 4.x das soluções do Experience Cloud.

## Métodos de configuração {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **DebugLogging**

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

   Se um identificador personalizado foi definido, retorna esse identificador. Se um identificador personalizado não estiver definido, retorna null. O valor padrão é `null`.

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

   Indica ao SDK que o aplicativo está pausado, a fim de calcular corretamente as medições de ciclo de vida. Por exemplo, ao pausar, um carimbo de data e hora é coletado para determinar a duração da sessão anterior. Isso também define um sinalizador para que o ciclo de vida saiba que o aplicativo não parou de funcionar. Para obter mais informações, consulte [Medições de ciclo de vida](/help/android/metrics.md).

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

   (4.2 ou posterior) Permite carregar um arquivo de configuração `ADBMobile JSON` diferente quando o aplicativo é iniciado. A configuração diferente é utilizada até o aplicativo ser fechado.

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

   (4.2 ou superior) Define o ícone grande usado para notificações criadas pelo SDK. Este ícone é a principal imagem exibida quando o usuário visualizar a notificação completa na central de notificações.

   * Esta é a sintaxe para este método:

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   (4.2 ou posterior) Define o ícone pequeno usado para notificações criadas pelo SDK. Esse ícone é exibido na barra de status e é a imagem secundária mostrada quando o usuário vê a notificação completa na central de notificações.

   * Esta é a sintaxe para este método:

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * Esta é a amostra de código para este método:

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Métodos do Analytics {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Retorna a ID gerada automaticamente para o Analytics. Esta é uma ID exclusiva específica do aplicativo gerada na primeira inicialização e armazenada e usada a partir desse ponto. Essa ID é preservada entre as atualizações do aplicativo e é removida durante a desinstalação.

   * Esta é a sintaxe para este método:

      ```java
      public static string TrackingIdentifier;
      ```

   * Esta é a amostra de código para este método:

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   Rastreia um estado de aplicativo com dados de contexto opcionais. `States` são as exibições disponíveis no aplicativo, como &quot;tela inicial&quot;, &quot;nível 1&quot;, &quot;pausa&quot; e assim por diante. Esses estados são semelhantes às páginas em um site, e as chamadas de `TrackState` aumentam as visualizações de página. Se state estiver vazio, ele é exibido como &quot;app name app version (build)&quot; nos relatórios. Caso veja esse valor em relatórios, certifique-se de configurar o estado em cada chamada de `TrackState`.

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

   Rastreia uma ação no seu aplicativo. As ações são coisas que ocorrem no seu aplicativo e que deseja medir, como &quot;mortes&quot;, &quot;nível obtido&quot;, &quot;assinaturas de feed&quot; e outras métricas.

   >[!TIP]
   >
   >
   >Se você tem um código que pode funcionar enquanto o aplicativo é executado em segundo plano (por exemplo, uma recuperação de dados em segundo plano), use `trackActionFromBackground`.

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

   Envia as coordenadas atuais de latitude e longitude. Também usa pontos de interesse definidos no arquivo `ADBMobileConfig.json` para determinar se o local fornecido como parâmetro está no POI. Se as coordenadas atuais estão dentro de um POI definido, uma variável de dados de contexto é preenchida e enviada com a chamada `TrackLocation`.

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

   Transmita dados para atualizar os dados de contexto associados a determinada ação. Os dados transmitidos são anexados aos existentes para a ação em questão e os substituem se a mesma chave já estiver definida para a ação.

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

   Força a biblioteca a enviar todas as ocorrências na fila offline, independentemente de quantas estejam na fila no momento.

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

## Métodos de ID do Experience Cloud {#section_157919E46030443DBB5CED60D656AD9F}

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

   Com a ID do Experience Cloud, é possível definir outras IDs do cliente para associar a cada visitante. A API de visitante aceita várias IDs do cliente para o mesmo visitante, juntamente com um identificador de tipo de cliente para separar o escopo de diferentes IDs do cliente. Este método corresponde a `setCustomerIDs` na biblioteca do JavaScript.

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

   Envia uma solicitação para o servidor do Target configurado e retorna o valor da cadeia de caracteres da oferta gerada em um retorno de chamada `Action<NSDictionary>`.

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

   O construtor de conveniência cria um objeto `ADBTargetLocationRequest` com os parâmetros fornecidos.

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

   Apaga os cookies do Target do seu aplicativo.

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

   Retorna o perfil do visitante obtido recentemente. Retorna nil se nenhum sinal tiver sido enviado. O perfil do visitante é salvo em `NSUserDefaults` para facilitar o acesso nas várias inicializações do aplicativo.

   * Esta é a sintaxe para este método:

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * Esta é a amostra de código para este método:

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   Retorna o `DPID` atual.

   * Esta é a sintaxe para este método:

      ```java
      public static string Dpuuid; 
      ```

   * Esta é a amostra de código para este método:

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **Dpuuid**

   Retorna o `DPUUID` atual.

   * Esta é a sintaxe para este método:

      ```java
      public static string AudienceDpuuid; 
      ```

   * Esta é a amostra de código para este método:

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **AudienceSetDpidAndDpuuid**

   Define os `dpid` e `dpuuid`. Se `dpid` e `dpuuid` estiverem definidas, elas serão enviadas com cada sinal.

   * Esta é a sintaxe para este método:

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * Esta é a amostra de código para este método:

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **SignalWithData**

   Envia ao gerenciamento de público-alvo um sinal com características e obtém os segmentos correspondentes retornados em um retorno de chamada `Action<NSDictionary>`.

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

   Redefine o Audience Manager `UUID` e limpa o perfil do visitante atual.

   * Esta é a sintaxe para este método:

      ```java
      public static void Reset ();
      ```

   * Esta é a amostra de código para este método:

      ```java
       AudienceManager.Reset ();
      ```

## Vídeo {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Para obter mais informações sobre o Video Analytics, consulte [Video Analytics](/help/android/analytics-main/video-qs.md).

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

* **Fechar**

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

   Reproduz o item de mídia com o nome nome no deslocamento em questão (em segundos).

   * Esta é a sintaxe para este método:

      ```java
      public static void Play ( string name, double offset); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **Concluído**

   Marca manualmente o item de mídia como concluído no offset em questão (em segundos).

   * Esta é a sintaxe para este método:

      ```java
      public static void Complete (string name, double offset); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **Stop**

   Notifica ao módulo de mídia que o vídeo foi interrompido ou pausado no offset em questão.

   * Esta é a sintaxe para este método:

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **Click**

   Notifica ao módulo de mídia que o item de mídia foi clicado.

   * Esta é a sintaxe para este método:

      ```java
      public static void Click ( string name, double offset); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **Track**

   Envia uma chamada de ação de rastreamento (sem exibição de página) para o estado de mídia atual.

   * Esta é a sintaxe para este método:

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.Track (settings.Name, null); 
      ```
