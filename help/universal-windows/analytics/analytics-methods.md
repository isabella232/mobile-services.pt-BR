---
description: Informações que o auxiliam a usar o SDK da plataforma Universal Windows no Adobe Analytics.
seo-description: Informações que o auxiliam a usar o SDK da plataforma Universal Windows no Adobe Analytics.
seo-title: Métodos do Analytics
solution: Marketing Cloud, Analytics
title: Métodos do Analytics
topic: Desenvolvedor e implementação
uuid: cc 299 bb 5-ec 61-49 bf -869 a-f 3 c 3 bc 83359 f
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

Informações que o auxiliam a usar o SDK da plataforma Universal Windows no Adobe Analytics.

O SDK atualmente é compatível com diversas Soluções da Adobe Experience Cloud, incluindo Analytics, Target e Audience Manager. Os métodos apresentam prefixos de acordo com a solução. Métodos do Analytics recebem o prefixo “Analytics”.

Cada um desses métodos é usado para enviar dados para seu conjunto de relatórios do Adobe Analytics.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **Trackstate (winjs: Trackstate)**

   Rastreia um estado de aplicativo com dados de contexto opcionais. Os estados são as visualizações que estão disponíveis no seu aplicativo, como “painel inicial”, “configurações do aplicativo”, “carrinho” e assim por diante. Esses estados são semelhantes às páginas em um site e as chamadas de `TrackState` aumentam as exibições de página.
Se `state` estiver vazio, ele é exibido como “app name app version (build)” nos relatórios. Se você encontrar esse valor nos relatórios, certifique-se de que esteja definindo `state` em cada chamada de `TrackState`.

   >[!TIP]
   >
   >Esta é a única chamada de rastreamento que aumenta as exibições de página.

   * Esta é a sintaxe para este método:

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **Trackaction (winjs: Trackaction)**

   Rastreia uma ação no seu aplicativo. As ações são coisas que ocorrem no seu aplicativo e que deseja avaliar, como “logons”, “toques em banners”, “assinaturas de feed” e outras métricas.

   * Esta é a sintaxe para este método:

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackAction("ButtonClick",null); 
      ```

* **Gettrackingidentifierasync (winjs: Gettrackingidentifierasync)**

   Retorna a ID de visitante gerada automaticamente para o Analytics. Esta é uma ID de visitante único e específica do aplicativo, gerada durante a primeira inicialização e, em seguida, armazenada e utilizada a partir desse ponto. Esta ID é preservada entre as atualizações do aplicativo e é removida durante a desinstalação.

   * Esta é a sintaxe para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String> ^GetTrackingIdentifierAsync(); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      vartrackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function(trackingid){
      trackingIdentifier=trackingid;
      });
      ```

* **Tracklocation (winjs: Tracklocation)**

   Envia as coordenadas x e y atuais. Também usa pontos de interesse definidos no arquivo `ADBMobileConfig.json` a fim de determinar se o local fornecido como parâmetro está dentro do POI. Se as coordenadas atuais estão dentro de um POI definido, uma variável de dados de contexto é preenchida e enviada com a chamada `trackLocation`.

   * Esta é a sintaxe para este método:

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData);
      ```

   * Esta é a amostra de código para este método:

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackLocation(47.60621,-122.33207,null);
      ```

* **Tracklifetimevalueincrease (winjs: Tracklifetimevalueincrease)**

   Adiciona uma `amount` ao valor do ciclo de vida do usuário.

   * Esta é a sintaxe para este método:

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackLifetimeValueIncrease(10,null);
      ```

* **Tracktimedactionstart (winjs: Tracktimedactionstart)**

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
      varADB=ADBMobile;
      ADB.Analytics.trackTimedActionStart("cartToCheckout",null); 
      ```

* **Tracktimedactionupdate (winjs: Tracktimedactionupdate)**

   Transmite `contextData` para atualizar os dados de contexto associados à `action`. The `data` passed in is appended to the existing data for the given action, and overwrites the data if the same key is already defined for `action`.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      varADB = ADBMobile;
      varcontextData = newWindows.Foundation.Collections.PropertySet();
      contextData["quantity"]=3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout",contextData);
      ```

* **Tracktimedactionexistsasync (winjs: Tracktimedactionexistsasync)**

   Retorna true se a ação cronometrada fornecida existir e false se ela não existir.

   * Esta é a sintaxe para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function(exists){ 
          actionExists = exists; 
      });
      ```

* **Tracktimedactionend (winjs: Tracktimedactionend)**

   Encerra uma ação programada.

   * Esta é a sintaxe para este método:

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * Esta é a amostra de código para este método:

      ```js
      varADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **Cleartrackingqueue (winjs: Cleartrackingqueue)**

   Limpa todas as ocorrências armazenadas na fila de rastreamento do Analytics.

   * Esta é a sintaxe para este método:

      ```csharp
      static void ClearTrackingQueue();
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **Getqueuesizeasync (winjs: Getqueuesizeasync)**

   Retorna o número de ocorrências armazenadas na fila do Analytics no momento.

   * Esta é a sintaxe para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * Esta é a amostra de código para este método:

      ```js
      varqueueSize;
      ADBMobile.Analytics.getQueueSizeAsync().then(function(size){ 
          queueSize=size;
      });
      ```
