---
description: Informações para ajudá-lo a usar o SDK da loja de aplicativos universal do Windows 8.1 com o Adobe Analytics.
seo-description: Informações para ajudá-lo a usar o SDK da loja de aplicativos universal do Windows 8.1 com o Adobe Analytics.
seo-title: Métodos do Analytics
solution: Marketing Cloud,Analytics
title: Métodos do Analytics
topic: Developer and implementation
uuid: 79db105c-216c-4061-97f3-a55954995e67
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 52%

---


# Métodos do Analytics {#analytics-methods}

Informações para ajudá-lo a usar o SDK da loja de aplicativos universal do Windows 8.1 com o Adobe Analytics.

O SDK suporta atualmente várias Soluções Adobe Experience Cloud, incluindo Analytics, Público alvo e Audience Manager. Os métodos apresentam prefixos de acordo com a solução. Métodos do Analytics recebem o prefixo &quot;Analytics&quot;.

Cada um desses métodos é usado para enviar dados para seu conjunto de relatórios do Adobe Analytics.

>[!TIP]
>
>Quando você consome `winmd` métodos do winJS (JavaScript), todos os métodos têm automaticamente a primeira letra em minúsculas.

* **TrackState (winJS: trackState)**

   Rastreia um estado de aplicativo com dados de contexto opcionais. Os estados são as visualizações que estão disponíveis no aplicativo, como &quot;painel inicial&quot;, &quot;configurações do aplicativo&quot;, &quot;carrinho&quot; e assim por diante. Esses estados são semelhantes às páginas em um site, e as chamadas de `TrackState` aumentam as visualizações de página. If `state` is empty, it displays as &quot;app name app version (build)&quot; in reports. If you see this value in reports, make sure you are setting `state` in each `TrackState` call.

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

   Rastreia uma ação no seu aplicativo. As ações são coisas que ocorrem no aplicativo e que você deseja avaliar, como &quot;logons&quot;, &quot;toques em banners&quot;, &quot;subscrições de feed&quot; e outras métricas.

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

   Retorna o identificador de visitante gerado automaticamente pelo Analytics. Esta é uma ID de visitante exclusiva específica do aplicativo que é gerada na primeira inicialização e, em seguida, armazenada e usada a partir desse ponto. Essa ID é preservada entre as atualizações do aplicativo e é removida na desinstalação.

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

   Transmite `contextData` para atualizar os dados de contexto associados à `action`. The `data` passed is appended to the existing data for the given action, and overwrites the data if the same key is already defined for `action`.

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

   Retorna true se a ação cronometrada especificada existir e false se não existir.

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

   Limpa todas as ocorrências armazenadas da fila de rastreamento do Analytics.

   * Esta é a sintaxe desta mensagem:

      ```csharp
      static void ClearTrackingQueue();
      ```

   * Esta é a amostra de código:

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync (winJS: getQueueSizeAsync)**

   Retorna o número de ocorrências armazenadas atualmente na fila do Analytics.

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
