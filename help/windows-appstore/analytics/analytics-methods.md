---
description: Informações para ajudá-lo a usar o SDK do Windows 8.1 Universal App Store com Adobe Analytics.
solution: Experience Cloud Services,Analytics
title: Métodos do Analytics
topic-fix: Developer and implementation
uuid: 79db105c-216c-4061-97f3-a55954995e67
exl-id: 007bb801-55ef-4c5b-87fa-d0db42cde163
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 53%

---

# Métodos do Analytics {#analytics-methods}

Informações para ajudá-lo a usar o SDK do Windows 8.1 Universal App Store com Adobe Analytics.

Atualmente, o SDK é compatível com várias soluções da Adobe Experience Cloud, incluindo o Analytics, o Target e o Audience Manager. Os métodos apresentam prefixos de acordo com a solução. Métodos do Analytics recebem o prefixo &quot;Analytics&quot;.

Cada um desses métodos é usado para enviar dados para seu conjunto de relatórios do Adobe Analytics.

>[!TIP]
>
>Ao consumir `winmd` métodos do winJS (JavaScript), todos os métodos passam a ter a primeira letra em minúsculas automaticamente.

* **TrackState (winJS: trackState)**

   Rastreia um estado de aplicativo com dados de contexto opcionais. Os estados são as exibições disponíveis no aplicativo, como &quot;painel inicial&quot;, &quot;configurações do aplicativo&quot;, &quot;carrinho&quot; e assim por diante. Esses estados são semelhantes às páginas em um site, e as chamadas de `TrackState` aumentam as visualizações de página. If `state` estiver vazio, é exibido como &quot;app name app version (build)&quot; nos relatórios. Caso veja esse valor em relatórios, certifique-se de configurar `state` em cada `TrackState` chame.

   >[!TIP]
   >
   >Esta é a única chamada de rastreamento que aumenta as exibições de página.

   * Esta é a sintaxe para este método:

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **TrackAction (winJS: trackAction)**

   Rastreia uma ação no seu aplicativo. As ações são coisas que ocorrem no seu aplicativo e que deseja medir, como &quot;logons&quot;, &quot;toques em banners&quot;, &quot;assinaturas de feed&quot; e outras métricas.

   * Esta é a sintaxe para este método:

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap <Platform::String^, Platform::Object> ^contextData);
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackAction("Button Click", null); 
      ```

* **GetTrackingIdentifierAsync (winJS: getTrackingIdentifierAsync)**

   Retorna o identificador de visitante gerado automaticamente pelo Analytics. Esta é uma ID de visitante exclusiva específica do aplicativo gerada na primeira inicialização e, em seguida, armazenada e usada a partir desse ponto. Essa ID é preservada entre as atualizações do aplicativo e é removida durante a desinstalação.

   * Esta é a sintaxe para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String^> ^GetTrackingIdentifierAsync(); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      var trackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function (trackingid) { 
         trackingIdentifier = trackingid; 
      });
      ```

* **TrackLocation (winJS: trackLocation)**

   Envia as coordenadas x e y atuais. Também usa pontos de interesse definidos no arquivo `ADBMobileConfig.json` a fim de determinar se o local fornecido como parâmetro está dentro do POI. Se as coordenadas atuais estão dentro de um POI definido, uma variável de dados de contexto é preenchida e enviada com a chamada `trackLocation`.

   * Esta é a sintaxe para este método:

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLocation(47.60621, -122.33207, null);
      ```

* **TrackLifetime &#x200B; ValueIncrease (winJS: trackLifetime &#x200B; ValueIncrease)**

   Adiciona uma `amount` ao valor do ciclo de vida do usuário.

   * Esta é a sintaxe para este método:

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLifetimeValueIncrease(10, null); 
      ```

* **TrackTimed &#x200B; ActionStart (winJS: trackTimed &#x200B; ActionStart)**

   Inicia uma ação programada com a `action` de nome. Se você chamar este método para uma ação já iniciada, a ação programada anterior será substituída.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```csharp
      static void TrackTimedActionStart(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionStart("cartToCheckout", null); 
      ```

* **TrackTimed &#x200B; ActionUpdate (winJS: trackTimed &#x200B; ActionUpdate)**

   Transmite `contextData` para atualizar os dados de contexto associados à `action`. O `data` transmitido está anexado aos dados existentes para a ação em questão e os substitui se a mesma chave já estiver definida para `action`.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile; 
      var contextData = new Windows.Foundation.Collections.PropertySet(); 
      contextData["quantity"] = 3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout", contextData); 
      ```

* **TrackTimedActionExistsAsync (winJS: trackTimedActionExistsAsync)**

   Retorna true se a determinada ação cronometrada existir e false se não existir.

   * Esta é a sintaxe para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function (exists) { 
          actionExists = exists; 
      });
      ```

* **TrackTimed &#x200B; ActionEnd (winJS: trackTimed &#x200B; ActionEnd)**

   Encerra uma ação programada.

   * Esta é a sintaxe para este método:

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **ClearTrackingQueue (winJS: clearTrackingQueue)**

   Apaga todas as ocorrências armazenadas da fila de rastreamento do Analytics.

   * Esta é a sintaxe desta mensagem:

      ```csharp
      static void ClearTrackingQueue();
      ```

   * Esta é a amostra de código:

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync (winJS: getQueueSizeAsync)**

   Retorna o número de ocorrências armazenadas na fila do Analytics no momento.

   * Esta é a sintaxe para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var queueSize; 
      ADBMobile.Analytics.getQueueSizeAsync().then(function (size) { 
          queueSize = size; 
      });
      ```
