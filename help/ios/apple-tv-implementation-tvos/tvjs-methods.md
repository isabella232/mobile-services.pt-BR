---
description: Esta é uma lista de métodos TVJS fornecidos pela biblioteca tvOS.
seo-description: Esta é uma lista de métodos TVJS fornecidos pela biblioteca tvOS.
seo-title: Métodos TVJS
solution: Marketing Cloud,Analytics
title: Métodos TVJS
topic: Desenvolvedor e implementação
uuid: a7bfa85a-0d6e-4f51-9a9e-70429c2a9806
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Métodos TVJS {#tvjs-methods}

Esta é uma lista de métodos TVJS fornecidos pela biblioteca tvOS.

## Configuration methods {#section_5F82FD2F6A0546B3B4E80DF832E11634}

* **version**

   Retorna a versão atual da biblioteca do Adobe Mobile.

   * Esta é a sintaxe para este método:

      ```objective-c
      version()
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      var sdkVersion = ADBMobile.version();
      ```

   * Devoluções: `String`

* **privacyStatus**

   Retorna a representação NSUInteger da enumeração do status de privacidade do usuário atual.

   Seguem os scripts:

   * `ADBMobilePrivacyStatusOptIn`: As ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut`: As ocorrências são descartadas.
   * `ADBMobilePrivacyStatusUnknown`: se o rastreamento offline estiver ativado, as ocorrências são salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas).

      Se o rastreamento offline não estiver ativado, as ocorrências são descartadas até o status de privacidade ser alterado para aceitar. THe default value is set in the `ADBMobileConfig.json` file.

   * Esta é a sintaxe para este método:

      ```objective-c
      privacyStatus()
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      var privacyStatus = ADBMobile.privacyStatus();
      ```

   * Devoluções: `Number`

* **setPrivacyStatus**

   Define o status de privacidade do usuário atual para um dos seguintes valores:

   * `ADBMobilePrivacyStatusOptIn`: Hits are sent immediately.
   * `ADBMobilePrivacyStatusOptOut`: Hits are discarded.
   * `ADBMobilePrivacyStatusUnknown`: Se o rastreamento offline estiver ativado, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas).
   Se o rastreamento offline não estiver ativado, as ocorrências são descartadas até o status de privacidade ser alterado para aceitar.

   * Esta é a sintaxe para este método:

      ```objective-c
      setPrivacyStatus(privacyStatus)
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```


* **lifetimeValue**

   Retorna o valor do tempo de vida do usuário atual. O valor padrão é `0`.

   * Esta é a sintaxe para este método:

      ```objective-c
      lifetimeValue()
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      var ltv = ADBMobile.lifetimeValue();
      ```

   * Devoluções: `Number`

* **userIdentifier**

   Retorna o identificador do usuário se algum identificador personalizado estiver configurado. Retorna nil se um identificador personalizado não estiver configurado. O padrão é `nil`.

   >[!IMPORTANT]
   >
   >If your app upgrades from the Experience Cloud 3.x to 4.x SDK, the previous custom or automatically generated visitor ID is retrieved and stored as the custom user identifier. Isso preserva os dados dos visitantes entre as atualizações de SDK. Para novas instalações no SDK 4.x, o identificador do usuário é nil até sua definição.

   * Esta é a sintaxe para este método:

      ```objective-c
      userIdentifier()
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      var uid = ADBMobile.userIdentifier();
      ```

   * Devoluções: `String`

* **setUserIdentifier**

   Define o identificador do usuário.

   * Esta é a sintaxe para este método:

      ```objective-c
      setUserIdentifier(userId)
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.setUserIdentifier(‘myUserId’);
      ```

   * Retorna: N/A

   * Parâmetro:  `userID`

      * Tipo: cadeia de caracteres
      * Novo identificador para este usuário.

* **setAdvertisingIdentifier**

   Define o IDFA no SDK e, se ele tiver sido definido no SDK, o IDFA será enviado no ciclo de vida. O IDFA também pode ser acessado em Sinais (Postbacks).

   >[!IMPORTANT]
   >
   >Retrieve the IDFA from Apple APIs only if you are using an ad service. Se você recuperar o IDFA e não o utilizar corretamente, seu aplicativo poderá ser rejeitado.

   * Esta é a sintaxe para este método:

      ```objective-c
      setAdvertisingIdentifier(idfa)
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.setAdvertisingIdentifier(‘myIdfa’);
      ```

   * Retorna: N/A
   * Parâmetro: `idfa`
      * Tipo: `String`
      * O IDFA recuperado da API da Apple.

* **setDebugLogging**

   Define a preferência de registro de depuração.

   * Esta é a sintaxe para este método:

      ```objective-c
      setDebugLogging(logging)
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      `ADBMobile.setDebugLogging(true);
      ```

   * Retorna: N/A
   * Parâmetros: `logging`
      * Tipo: `Bool`
      * Valor que indica se o SDK da Adobe deve registrar no console de depuração.


## Analytics methods {#section_F3DB9BE225F84F86BE5F8D15164C0379}

* **trackStateData**

   Rastreia um estado de aplicativo com dados de contexto opcionais. Os estados são as visualizações que estão disponíveis no seu aplicativo, como o painel de entrada, as configurações do aplicativo, o carrinho e assim por diante. Esses estados são semelhantes às páginas em um site e as chamadas de trackState aumentam as exibições de página.

   Se o estado estiver vazio, será exibido como app name app version (build) nos relatórios. Caso veja esse valor em relatórios, certifique-se de configurar o estado em cada chamada de trackState.

   >[!TIP]
   >
   >This is the only tracking call that increments page views.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackStateData(stateName [, contextData])
      ```

      * Retorna: N/A
      * Parâmetro: `stateName`
         * Tipo: `String`
         * Nome do estado da página
      * Parâmetro: `contextData`
         * Tipo: objeto
         * Dados de contexto adicionais para esta ocorrência.
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.trackStateData(‘homepage’, {‘userid’:12345});
      ```




* **trackActionData**

   Rastreia uma ação no seu aplicativo. As ações são coisas que ocorrem no seu aplicativo e que deseja avaliar, como logons, toques em banners, assinaturas de feed e outras métricas.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackActionData(actionName [, contextData])
      ```

      * Retorna: N/A
      * Parâmetros: `actionName`
         * Tipo: cadeia de caracteres
         * Nome da ação que está sendo rastreada.
      * Parâmetro: `contextData`
         * Tipo: objeto
         * Dados de contexto adicionais para esta ocorrência.
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.trackActionData(‘likeClicked’, {‘imageName’:’funnyKitty’});
      ```



* **trackLocationWithLatLonData**

   Envia as coordenadas atuais de latitude e longitude.

   Also uses points of interest (POI) that are defined in the `ADBMobileConfig.json` file to determine whether the location that you entered as a parameter is in any of your POIs. Se as coordenadas atuais estão dentro de um POI definido, uma variável de dados de contexto é preenchida e enviada com a chamada `trackLocation`.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackLocationWithLatLonData(lat, lon [, contextData]);
      ```

      * Retorna: N/A
      * Parâmetro: `lat`
         * Tipo: número
         * Latitude da localização.
      * Parâmetro: `lon`
         * Tipo: número
         * Longitude da localização.
      * Parâmetro: `contextData`
         * Tipo: objeto
         * Dados de contexto adicionais para esta ocorrência.
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.trackLocationWithLatLonData(43.36, -116.12, null);
      ```




* **trackLifetimeValueIncreaseJsData**

   Adiciona uma quantia ao valor do ciclo de vida do usuário.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackLifetimeValueIncreaseJsData(increaseAmount)
      ```

      * Retorna: N/A
      * Parâmetro: `increaseAmount`
         * Tipo: número
         * Quantidade para adicionar ao valor atual do ciclo de vida do usuário.
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.trackLifetimeValueIncreaseJsData(5);
      ```


* **trackTimedActionStartData**

   Inicia uma ação programada com a ação de nome. Se você chamar este método para uma ação já iniciada, a ação programada anterior será substituída.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackTimedActionStartData(name [, contextData])
      ```

      * Retorna: N/A
      * Parâmetro: `name`
         * Tipo: cadeia de caracteres
         * Nome da ação cronometrada que está sendo iniciada.
      * Parâmetro: `contextData`
         * Tipo: objeto
         * Dados de contexto adicionais para esta ocorrência.
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.trackTimedActionStartData(‘level1’, {‘userId’:42423});
      ```


* **trackTimedActionUpdateData**

   Repassa os dados para atualizar os dados de contexto associados à ação.

   Os dados transmitidos são anexados aos dados existentes para a ação em questão e, se a mesma chave já estiver definida para ação, os dados são substituídos.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackTimedActionUpdateData(name [, contextData])
      ```

      * Retorna: N/A
      * Parâmetro: `name`
         * Tipo: cadeia de caracteres
         * Nome da ação cronometrada que está sendo atualizada.
      * Parâmetro: `contextData`
         * Tipo: objeto
         * Dados de contexto adicionais para esta ocorrência.
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.trackTimedActionUpdateData(‘level1’);
      ```



* **trackTimedActionEndJsLogic**

   Encerra uma ação programada.

   Se você fornecer uma função de retorno de chamada, poderá acessar os valores de tempo finais. Se nenhum retorno de chamada for fornecido, ou se o retorno de chamada retornar verdadeiro, o SDK da Adobe enviará automaticamente uma ocorrência. Quando um falso é retornado do retorno de chamada, a ocorrência da ação cronometrada é suprimida.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackTimedActionEndJsLogic(name [, callback])
      ```

      * Retorna: N/A
      * Parâmetros: `name`
         * Tipo: cadeia de caracteres
         * Nome da ação cronometrada a ser encerrada
      * Parâmetro: `callback`
         * Tipo: `function(inAppDuration, totalDuration, data)`
         * Callback method that will have `inAppDuration` (number), `totalDuration` (number), and `data` (context data object) in its parameters.

            You can suppress the final hit from being sent by the SDK by returning `false` in your callback function.
      * Esta é a amostra de código para este método:

         ```objective-c
         ADBMobile.trackTimedActionEndJsLogic(‘level1’, 
         function(inAppDuration, totalDuration, data) {
             // do something with final values
             return true;
             });
         ```



* **trackingTimedActionExistsJs**

   Retorna se uma ação cronometrada estiver em andamento.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackingTimedActionExistsJs(name)
      ```

      * Retorna: Bool
      * Parâmetro: `name`
         * Tipo: `String`
         * Nome da ação cronometrada para a qual você precisa verificar a existência.
   * Esta é a amostra de código para este método:


      ```objective-c
      var actionExists = ADBMobile.trackTimedActionExistsJs(‘level1’);
      ```


* **trackingIdentifier**

   Retorna o identificador de visitante gerado automaticamente.

   Esta é uma ID de visitante único específica do aplicativo, gerada pelos servidores da Adobe. Se os servidores da Adobe não puderem ser alcançados no momento da geração, a ID será gerada usando a CFUUID da Apple. O valor é gerado na primeira inicialização e é armazenado e usado a partir desse ponto. Essa ID é preservada entre as atualizações de aplicativos, é salva e restaurada durante o processo padrão de backup de aplicativos e é removida quando o aplicativo for desinstalado.

   >[!TIP]
   >
   >Se seu aplicativo for atualizado do SDK 3.x da Experience Cloud para o 4.x, a ID de visitante personalizada ou gerada automaticamente anterior será recuperada e armazenada como o identificador de usuário personalizado. Isso preserva os dados dos visitantes entre as atualizações de SDK. Para novas instalações no SDK 4.x, o identificador do usuário é `nil` e o identificador de rastreamento é usado. Para obter mais informações, consulte a linha userIdentifier abaixo.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackingIdentifier()
      ```

      * Devoluções: `String`
      * Parâmetros: nenhum
   * Esta é a amostra de código para este método:

      ```objective-c
      var trackingId = ADBMobile.trackingIdentifier();
      ```


* **trackingSendQueuedHits**

   Força a biblioteca a enviar todas as ocorrências na fila offline, independentemente de quantas estão na fila no momento.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackingSendQueuedHits()
      ```

      * Retorna: N/A
      * Parâmetros: nenhum
   * Esta é a amostra de código para este método:


      ```objective-c
      ADBMobile.trackingSendQueuedHits();
      ```


* **trackingClearQueue**

   Apaga todas as ocorrências da fila offline.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackingClearQueue()
      ```

      * Retorna: N/A
      * Parâmetros: nenhum
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.trackingClearQueue();
      ```


* **trackingGetQueueSize**

   Recupera o número de ocorrências na fila offline.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackingGetQueueSize()
      ```

      * Retorna: número
      * Parâmetros: nenhum
   * Esta é a amostra de código para este método:

      ```objective-c
      var queueSize = ADBMobile.trackingGetQueueSize();
      ```


## Audience Manager methods {#section_0155C4DF04644EDAAF6159C420A158DE}

* **audienceVisitorProfile**

   Retorna o perfil do visitante obtido recentemente.

   Retorna null se nenhum sinal tiver sido enviado. O perfil do visitante é salvo em `NSUserDefaults` para facilitar o acesso nas várias inicializações do aplicativo.

   * Esta é a sintaxe para este método:

      ```objective-c
      audienceVisitorProfile()
      ```

      * Retorna: objeto
      * Parâmetros: nenhum
   * Esta é a amostra de código para este método:

      ```objective-c
      var profile = ADBMobile.audienceVisitorProfile();
      ```


* **audienceDpid**

   Retorna a DPID atual.

   * Esta é a sintaxe para este método:

      ```objective-c
      audienceDpid()
      ```

      * Retorna: cadeia de caracteres
      * Parâmetros: nenhum
   * Esta é a amostra de código para este método:

      ```objective-c
      var dpid = ADBMobile.audienceDpid();
      ```


* **audienceDpuuid**

   Retorna a DPUUID atual.

   * Esta é a sintaxe para este método:

      ```objective-c
      audienceDpuuid()
      ```

      * Devoluções: `String`
      * Parâmetros: nenhum
   * Esta é a amostra de código para este método:

      ```objective-c
      var dpuuid = ADBMobile.audienceDpuuid();
      ```


* **audienceSetDpidDpuuid**

   Define a dpid e a dpuuid e, se estiverem configuradas, serão enviadas com cada sinal.

   * Esta é a sintaxe para este método:

      ```objective-c
      audienceSetDpidDpuuid(dpid, dpuuid)
      ```

      * Retorna: N/A
      * Parâmetro: `dpid`
         * Tipo: `String`
         * ID do provedor de dados do Audience Manager.
      * Parâmetro: `dpuuid`
         * Tipo: `String`
         * Identificador para a combinação de usuário e provedor de dados.
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.audienceSetDpidDpuuid(‘myDpid’, ‘userDpuuid’);
      ```


* **audienceSignalWithDataJsCallback**

   Envia ao Audience Manager um sinal com características e obtém os segmentos correspondentes que são retornados em uma função de retorno de chamada.

   * Esta é a sintaxe para este método:

      ```objective-c
      audienceSignalWithDataJsCallback(traits [, callback])
      ```

      * Parâmetro: `traits`
         * Tipo: objeto
         * Dicionário de características para este usuário.
      * Parâmetro: `callback`
         * Tipo: function(profile)
         * O perfil retornado do Audience Manager no parâmetro para a função de retorno de chamada.
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.audienceSignalWithDataJsCallback({‘trait’:’something’}, 
      function(profile) {
          //do something with the user’s segments found in profile
           });
      ```



* **audienceReset**

   Restaura o UUID do Audience Manager e elimina o perfil do visitante atual.

   * Esta é a amostra de código para este método:

      ```objective-c
      audienceReset()
      ```

      * Retorna: N/A
      * Parâmetro: Nenhum
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.audienceReset();
      ```


## ID Service methods {#section_BEB6DA612EA4423FB354B65ECC941335}

* **visitorMarketingCloudID**

   Recupera a Experience Cloud ID a partir do serviço de ID.

   * Esta é a sintaxe para este método:

      ```objective-c
      visitorMarketingCloudID()
      ```

      * Retorna: cadeia de caracteres
      * Parâmetros: nenhum
   * Esta é a amostra de código para este método:

      ```objective-c
      var mcid = ADBMobile.visitorMarketingCloudID();
      ```


* **visitorSyncIdentifiers**

   Além da Experience Cloud ID, é possível configurar IDs de clientes adicionais para serem associadas a cada visitante. A API de visitante aceita várias IDs do cliente para o mesmo visitante, juntamente com um identificador de tipo de cliente para separar o escopo de diferentes IDs do cliente. Este método corresponde a setCustomerIDs na biblioteca do JavaScript.

   * Esta é a sintaxe para este método:

      ```objective-c
      visitorSyncIdentifiers(identifiers)
      ```

      * Retorna: N/A
      * Parâmetro: `identifiers`

         * Tipo: `Object`
         * Identificadores para sincronização com o serviço de ID para este usuário.
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.visitorSyncIdentifiers({‘idType’:’idValue’});
      ```


* **visitorSyncIdentifiersAuthenticationState**

   Sincroniza os identificadores fornecidos ao serviço de ID.

   * Esta é a sintaxe para este método:

      ```objective-c
      visitorSyncIdentifiersAuthenticationState(identifiers, authState)
      ```

      * Retorna: N/A
      * Parâmetros: `identifiers`
         * Tipo: `Object`
         * Identificadores para sincronização com o serviço de ID para este usuário.
      * Parâmetro: `authState`
         * Tipo: ADBMobileVisitorAuthenticationState
         * O estado de autenticação do usuário e os possíveis valores incluem:
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.visitorSyncIdentifiersAuthenticationState({'myIdType':'valueForUser'}, ADBMobileVisitorAuthenticationStateLoggedOut)
      ```



* **visitorSyncIdentifierWithTypeIdentifierAuthenticationState**

   Sincroniza o tipo de identificador e o valor fornecidos ao serviço de ID.

   * Esta é a sintaxe para este método:

      ```objective-c
      visitorSyncIdentifierWithTypeIdentifierAuthenticationState(idType, identifier, authState)
      ```

      * Retorno: N/A
      * Parâmetro: `idType`
         * Tipo: `String`
         * Tipo de identificador que você está sincronizando.
      * Parâmetro: `identifier`
         * Tipo: `String`
         * Valor do identificador que você está sincronizando.
      * Parâmetro: `authState`
         * Tipo: Estado ADBMobileVisitorAuthenticationStateAuthentication do usuário. Os valores possíveis incluem:
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.visitorSyncIdentifierWithTypeIdentifierAuthenticationState('myIdType', 'valueForUser', 
      ADBMobileVisitorAuthenticationStateAuthenticated);
      ```


* **visitorGetIDsJs**

   Obtém uma matriz de objetos ADBVisitorID somente leitura. O código a seguir é um exemplo de um objeto VisitorID:

   ```js
   {
       idType: "abc",
       authenticationState: 1, 
       identifier: "123"
   }
   ```

   * Esta é a sintaxe para este método:

      ```objective-c
      visitorGetIDsJs()
      ```

      * Devoluções: `Array [Object]`

      * Parâmetros: nenhum
   * Esta é a amostra de código para este método:

      ```objective-c
      var myVisitorIds = ADBMobile.visitorGetIDsJs();
      ```


## Métodos do Target {#section_F9F7EC2B9B7C41AFBCA2458F9F138634}

* **targetThirdPartyID**

   Retorna a ID de terceiros.

   * Esta é a sintaxe para este método:

      ```objective-c
      targetThirdPartyID()
      ```

      * Devoluções: `String`
      * Parâmetros: nenhum
   * Esta é a amostra de código para este método:

      ```objective-c
      var thirdPartyID = ADBMobile.targetThirdPartyID();
      ```


* **targetSetThirdPartyID**

   Define a ID de terceiros.

   * Esta é a sintaxe para este método:

      ```objective-c
      targetSetThirdPartyID(thirdPartyID)
      ```

      * Retorna: N/A
      * Parâmetros: `thirdPartyID`
         * Tipo: `String`
         * A ID de terceiros a usar para solicitações de destino.
   * Esta é a amostra de código para este método:
   ```objective-c
   ADBMobile.targetSetThirdPartyID(‘thirdPartyID’);
   ```

* **targetPcID**

   Retorna a PcID.

   * Esta é a sintaxe para este método:

      ```objective-c
      targetPcID()
      ```

      * Devoluções: `String`
      * Parâmetros: nenhum
   * Esta é a amostra de código para este método:

      ```objective-c
      var pcID = ADBMobile.targetPcID();
      ```


* **targetSessionID**

   Retorna a ID da sessão.

   * Esta é a sintaxe para este método:

      ```objective-c
      targetSessionID()
      ```

      * Devoluções: `String`
      * Parâmetros: nenhum
   * Esta é a amostra de código para este método:

      ```objective-c
      var sessionID = ADBMobile.targetSessionID();
      ```
