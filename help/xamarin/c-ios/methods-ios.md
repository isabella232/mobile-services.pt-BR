---
description: Métodos do iOS para componentes do Xamarin para SDK 4.x das soluções do Experience Cloud.
keywords: Xamarin
seo-description: Métodos do iOS para componentes do Xamarin para SDK 4.x das soluções do Experience Cloud.
seo-title: Métodos do iOS
solution: Experience Cloud
title: Métodos do iOS
uuid: d6a056db-80c1-44d0-970f-c961ad01b0bc
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1749'
ht-degree: 70%

---


# Métodos do iOS{#ios-methods}

Métodos do iOS para componentes do Xamarin para SDK 4.x das soluções do Experience Cloud.

## Métodos de configuração {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **CollectLifecycleData**

   Indica ao SDK que os dados do ciclo de vida devem ser coletados para uso em todas as soluções no SDK. Para obter mais informações, consulte [Medições de ciclo de vida](/help/ios/metrics.md).

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void CollectLifecycleData();
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.CollectLifecycleData();
      ```

* **DebugLogging**

   Retorna a preferência de log para a depuração atual. O valor padrão é `false`.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static bool DebugLogging(); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      var debugEnabled = ADBMobile.DebugLogging();
      ```

* **SetDebugLogging**

   Define a preferência de registro de depuração como ativada.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void SetDebugLogging(bool enabled);
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.SetDebugLogging(true);
      ```

* **LifetimeValue**

   Retorna o valor do tempo de vida do usuário atual.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static double LifetimeValue();
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      var lifetimeValue = ADBMobile.LifetimeValue();
      ```

* **PrivacyStatus**

   Retorna a representação de enumeração do status de privacidade do usuário atual.
   * `ADBMobilePrivacyStatus.OptIn` - as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatus.OptOut` - as ocorrências serão descartadas.
   * ADBMobilePrivacyStatus.Unknown - se o rastreamento offline estiver ativado, as ocorrências são salvas até o status de privacidade ser alterado para aceitar (e então as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o rastreamento offline estiver desativado, as ocorrências serão descartadas até que o status de privacidade seja alterado para opt in.

   The default value is set in the [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md).

   * Esta é a sintaxe para este método:

      ```objective-c
      public static ADBPrivacyStatus PrivacyStatus();
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      var privacyStatus = ADBMobile.PrivacyStatus();
      ```


* **SetPrivacyStatus**

   Define o status de privacidade do usuário atual como status. É definido como um dos valores abaixo:
   * `ADBMobilePrivacyStatus.OptIn` - as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatus.OptOut` - as ocorrências serão descartadas.
   * `ADBMobilePrivacyStatus.Unknown`  - se o rastreamento offline estiver ativado, as ocorrências são salvas até o status de privacidade ser alterado para aceitar (e então as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o rastreamento offline não estiver ativado, as ocorrências são descartadas até o status de privacidade ser alterado parar aceitar.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void SetPrivacyStatus(ADBPrivacyStatus status) 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.SetPrivacyStatus(ADBMobilePrivacyStatus.OptIn); 
      ```

* **UserIdentifier**

   Retorna o identificador de usuário personalizado se um identificador personalizado tiver sido definido. Retorna null se um identificador personalizado não estiver definido. O valor padrão é `null`.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static string UserIdentifier(); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      var userId = ADBMobile.UserIdentifier(); 
      ```

* **SetUserIdentifier**

   Retorna o identificador de usuário personalizado se um identificador personalizado tiver sido definido. Retorna null se um identificador personalizado não estiver definido. O valor padrão é `null`.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static string UserIdentifier();
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.SetUserIdentifier ("customUserIdentifier”); 
      ```

* **GetVersion**

   Obtém a versão da biblioteca.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static string Version();
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      var version = ADBMobile.Version();
      ```

* **KeepLifecycleSessionAlive (somente iOS)**

   Indica ao SDK que o próximo resumo em segundo plano não deve iniciar uma nova sessão, independentemente do tempo limite de valor da sessão do ciclo de vida presente no arquivo de configuração.

   >[!TIP]
   >
   >Este método é destinado a aplicativos que se registram para receber notificações enquanto estão em segundo plano e só deve ser chamado a partir do código executado enquanto o aplicativo está em segundo plano.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void KeepLifecycleSessionAlive();
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.KeepLifecycleSessionAlive();
      ```

## Métodos do Analytics {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Recupera o identificador do rastreamento de análises.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static string TrackingIdentifier();
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      var trackingId = ADBMobile.TrackingIdentifier();
      ```

* **TrackState**

   Rastreia um estado de aplicativo com dados de contexto opcionais. Os estados são as visualizações que estão disponíveis no aplicativo, como &quot;tela de título&quot;, &quot;nível 1&quot;, &quot;pausa&quot; e assim por diante. Esses estados são semelhantes às páginas em um site, e `TrackState` as chamadas incrementam as visualizações da página.Se o estado estiver vazio, ele será exibido como &quot;app name app version (build)&quot; nos relatórios. If you see this value in reports, make sure you are setting state in each `TrackState` call.

   >[!TIP]
   >
   >Esta é a única chamada de rastreamento que aumenta as exibições de página.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void TrackState(string state, NSDictionary cdata); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSDictionary contextData; 
       contextData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val"),NSObject.FromObject("key")); 
        ADBMobile.TrackState("title screen", contextData); 
      ```

* **TrackAction**

   Rastreia uma ação no seu aplicativo. As ações são coisas que ocorrem no aplicativo e que você deseja avaliar, como &quot;mortes&quot;, &quot;nível ganho&quot;, &quot;subscrições de feed&quot; e outras métricas.

   >[!TIP]
   >
   >Se você tem um código que pode funcionar enquanto o aplicativo é executado em segundo plano (por exemplo, uma recuperação de dados em segundo plano), use `trackActionFromBackground`.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void TrackAction(string action, NSDictionary cdata); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground (somente iOS)**

   Rastreia uma ação que ocorreu em segundo plano. Impede que os eventos do ciclo de vida sejam acionados em determinados cenários.

   >[!TIP]
   >
   > Este método deve ser chamado somente no código em execução enquanto o aplicativo estiver em segundo plano.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void TrackActionFromBackground(string action, NSDictionary cdata); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Envia as coordenadas atuais de latitude e longitude. Também usa pontos de interesse definidos no arquivo `ADBMobileConfig.json` a fim de determinar se o local fornecido como parâmetro está dentro do POI. Se as coordenadas atuais estão dentro de um POI definido, uma variável de dados de contexto é preenchida e enviada com a chamada `TrackLocation`.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void TrackLocation(CLLocation location, NSDictionary cdata); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      CoreLocation.CLLocation l = new CoreLocation.CLLocation  (111.111, 44.156);
      ADBMobile.TrackLocation (l, null);
      ```

* **TrackBeacon**

   Rastreia quando um usuário está perto de um beacon.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void TrackBeacon( CLBeacon beacon, NSDictionary cdata);
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      CoreLocation.CLBeacon beacon = new CoreLocation.CLBeacon (); 
      ADBMobile.TrackBeacon (beacon, null);
      ```

* **TrackingClearCurrentBeacon**

   Apaga os dados de beacons depois que o usuário se distancia de um.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void TrackingClearCurrentBeacon();
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   Adiciona valor ao valor do tempo de vida do usuário.

   * Esta é a sintaxe para este método:

      public nbsp;static void TrackLifetimeValueIncrease(quantia de duplo, dados NSDictionary);

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   Inicia uma ação programada com a ação de nome. Se você chamar este método para uma ação já iniciada, a ação programada anterior será substituída.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void TrackTimedActionStart(string action, NSDictionary cdata); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Transmita os dados para atualizar os dados de contexto associados à ação em questão. Os dados transmitidos são anexados aos dados existentes para a ação em questão e os substituem se a mesma chave já estiver definida para a ação.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void TrackTimedActionUpdate(string action, NSDictionary cdata); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSDictionary updatedData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val2"), NSObject.FromObject ("key2")); 
        ADBMobile.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   Encerra uma ação programada.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void TrackTimedActionEnd(string action, Func<double, double, NSMutableDictionary, sbyte> block); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("level2", (double  arg1,  double  arg2,  NSMutableDictionary  arg3)  =>  { 
      return  Convert.ToSByte(true); 
      });
      ```

* **TrackingTimedActionExists**

   Retorna se uma ação cronometrada está (ou não) em andamento.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("timedAction",  (double  inAppDuration, 
      double  totalDuration,  NSMutableDictionary  data)  =>  { 
                   return  true; 
      });
      ```

* **TrackingSendQueuedHits**

   Força a biblioteca a enviar todas as ocorrências na fila offline, independentemente de quantas estão na fila no momento.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void TrackingSendQueuedHits();
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   Apaga todas as ocorrências da fila offline.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void TrackingClearQueue(); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
       ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   Recupera o número de ocorrências na fila offline.

   * Esta é a amostra de código para este método:

      ```objective-c
      public static int TrackingGetQueueSize();
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      var queueSize = ADBMobile.TrackingGetQueueSize(); 
      ```

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

* **GetMarketingCloudID**

   Recupera a Experience Cloud ID a partir do serviço de ID.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static string GetMarketingCloudID(); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Com a ID do Experience Cloud, é possível definir outras IDs do cliente para associar a cada visitante. A API de Visitante aceita várias IDs do cliente para o mesmo visitante, juntamente com um identificador de tipo de cliente para separar o escopo de diferentes IDs do cliente. Este método corresponde a setCustomerIDs na biblioteca do JavaScript.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void VisitorSyncIdentifiers(NSDictionary identifiers);
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSDictionary  ids  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("pushID")); 
      ADBMobile.VisitorSyncIdentifiers(ids); 
      ```

## Métodos do Target {#section_C1E4121CAF9D43538511D857A1F549A7}

* **TargetLoadRequest**

   Sends request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void TargetLoadRequest (ADBTargetLocationRequest request, Action<NSString> callback); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ADBMobile.TargetLoadRequest(req,    (context)  =>  { 
      Console.WriteLine  (context); 
      });
      ```

* **TargetCreateRequest**

   Convenience constructor to create an `ADBTargetLocationRequest` object with the given parameters.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ```

* **TargetCreateOrderConfirmRequest**

   Cria um `ADBTargetLocationRequest`.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters);
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.TargetCreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **TargetClearCookies**

   Apaga quaisquer cookies de destino do seu aplicativo.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void TargetClearCookies(); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.TargetClearCookies(); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **AudienceVisitorProfile**

   Retorna o perfil do visitante obtido recentemente. Retorna nil se nenhum sinal tiver sido enviado ainda. Visitor profile is saved in `NSUserDefaults` for easy access across multiple launches of your app.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static NSDictionary AudienceVisitorProfile (); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSDictionary profile = ADBMobile.AudienceVisitorProfile();
      ```

* **AudienceDpid**

   Retorna a DPID atual.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static string AudienceDpid ();
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      string currentDpid = ADBMobile.AudienceDpid();
      ```

* **AudienceDpuuid**

   Retorna a DPUUID atual.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static string AudienceDpuuid ();
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      string currentDpuuid = ADBMobile.AudienceDpuuid(); 
      ```

* **AudienceSetDpidAndDpuuid**

   Define dpid e dpuuid. Se dpid e dpuuid estiverem definidas, elas serão enviadas com cada sinal.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void AudienceSetDpidAndDpuuid (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.AudienceSetDpidAndDpuuid ("testDppid", "testDpuuid")
      ```

* **AudienceSignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>`  callback.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void AudienceSignalWithData (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSDictionary  audienceData  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBMobile.AudienceSignalWithData  (audienceData,  (context)  =>  { 
      Console.WriteLine  (context); 
      }); 
      ```

* **AudienceReset**

   Redefine a UUID do Audience Manager e limpa o perfil de visitante atual.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void AudienceReset ();
      ```

   * Esta é a sintaxe para este método:

      ```objective-c
      ADBMobile.AudienceReset ();
      ```

## Vídeo {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Para obter mais informações, consulte Análise [de](/help/ios/getting-started/dev-qs.md)vídeo.

* **MediaCreateSettings**

   Retorna um objeto `ADBMediaSettings` com parâmetros especificados.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static ADBMediaSettings MediaCreateSettings ([string name, double length, string playerName, string playerID); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings ("name1", 10, "playerName1", "playerID1"); 
      ```

* **MediaAdCreateSettings**

   Retorna um objeto `ADBMediaSettings` a ser utilizado no rastreamento de um vídeo de anúncio.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static ADBMediaSettings MediaAdCreateSettings ( string name,  double length,  string playerName,  string parentName,  string parentPod,  double parentPodPosition,  string CPM); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMediaSettings adSettings = ADBMobile.MediaAdCreateSettings("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1");
      ```

* **MediaOpenWithSettings**

   Abre um objeto `ADBMediaSettings` para rastreamento.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void MediaOpenWithSettings ( ADBMediaSettings settings,  Action<ADBMediaState> callback); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings  ("name1",  10,  "playerName1",  "playerID1"); 
      ADBMobile.MediaOpenWithSettings  (settings,  (state)  =>  { 
      Console.WriteLine  (state.Name); 
      }); 
      ```

* **MediaClose**

   Fecha o item de mídia com nome.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void MediaClose ( string name);
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.MediaClose  (settings.Name);
      ```

* **MediaPlay**

   Reproduz o item de mídia com o nome nome no deslocamento em questão (em segundos).

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void MediaPlay ( string name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.MediaPlay (settings.Name, 0); 
      ```

* **MediaComplete**

   Marca manualmente o item de mídia como concluído no offset em questão (em segundos).

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void MediaComplete ( string name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.MediaComplete (settings.Name, 5);
      ```

* **MediaStop**

   Notifica ao módulo de mídia que o vídeo foi interrompido ou pausado no offset em questão.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void MediaStop ( string name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.MediaStop (settings.Name, 3);
      ```

* **MediaClick**

   Notifica ao módulo de mídia que o item de mídia foi clicado.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void MediaClick ( string name, double offset); 
      ```

* **MediaTrack**

   Envia uma chamada de ação de rastreamento (sem exibição de página) para o estado de mídia atual.

   * Esta é a sintaxe para este método:

      ```objective-c
      public static void MediaTrack ( string name, NSDictionary data); 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
       ADBMobile.MediaTrack (settings.Name, null);
      ```
