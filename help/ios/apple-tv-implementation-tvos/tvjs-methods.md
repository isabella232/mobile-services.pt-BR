---
description: Esta é uma lista de métodos TVJS fornecidos pela biblioteca tvOS.
solution: Experience Cloud,Analytics
title: Métodos TVJS
topic-fix: Developer and implementation
uuid: a7bfa85a-0d6e-4f51-9a9e-70429c2a9806
exl-id: 4e0c6a29-953d-49fc-b44f-533dd393ffb1
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '1997'
ht-degree: 100%

---

# Métodos TVJS {#tvjs-methods}

Esta é uma lista de métodos TVJS fornecidos pela biblioteca tvOS.

## Métodos de configuração {#section_5F82FD2F6A0546B3B4E80DF832E11634}

* **versão**

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

   Retorna a representação NSUInteger do enum de status de privacidade para o usuário atual.

   Estas são as opções:

   * `ADBMobilePrivacyStatusOptIn`: as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut`: as ocorrências são descartadas.
   * `ADBMobilePrivacyStatusUnknown`: se o rastreamento offline estiver ativado, as ocorrências são salvas até o status de privacidade ser alterado para “aceitar” (as ocorrências são enviadas) ou “recusar” (as ocorrências são descartadas).

      Se o rastreamento offline não estiver ativado, as ocorrências são descartadas até o status de privacidade ser alterado para aceitar. O valor por padrão está definido no arquivo `ADBMobileConfig.json`.

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

   * `ADBMobilePrivacyStatusOptIn`: as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut`: as ocorrências são descartadas.
   * `ADBMobilePrivacyStatusUnknown`: se o rastreamento offline estiver ativado, as ocorrências são salvas até o status de privacidade ser alterado para “aceitar” (as ocorrências são enviadas) ou “recusar” (as ocorrências são descartadas).

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
   >Se seu aplicativo for atualizado do SDK 3.x da Experience Cloud para o 4.x, a ID anterior de visitante, personalizada ou gerada automaticamente, será recuperada e armazenada como o identificador personalizado do usuário. Isso preserva os dados dos visitantes entre as atualizações de SDK. Para novas instalações no SDK 4.x, o identificador do usuário é nil até sua definição.

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

      * Tipo: String
      * Novo identificador para este usuário.

* **setAdvertisingIdentifier**

   Define o IDFA no SDK e, se tiver sido definido no SDK, o IDFA será enviado no ciclo de vida. O IDFA também pode ser acessado em Sinais (Postbacks).

   >[!IMPORTANT]
   >
   >Recupere o IDFA das APIs da Apple somente se estiver usando um serviço de anúncios. Se você recuperar o IDFA e não o utilizar corretamente, seu aplicativo poderá ser rejeitado.

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


## Métodos do Analytics {#section_F3DB9BE225F84F86BE5F8D15164C0379}

* **trackStateData**

   Rastreia um estado de aplicativo com dados de contexto opcionais. Os estados são as visualizações que estão disponíveis no seu aplicativo, como o painel de entrada, as configurações do aplicativo, o carrinho e assim por diante. Esses estados são semelhantes às páginas em um site, e as chamadas de trackState aumentam as exibições de página.

   Se o estado estiver vazio, será exibido como app name app version (build) nos relatórios. Caso veja esse valor em relatórios, certifique-se de configurar o estado em cada chamada de trackState.

   >[!TIP]
   >
   >Esta é a única chamada de rastreamento que aumenta as exibições de página.

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
         * Tipo: string
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

   Também usa pontos de interesse (POIs) definidos no arquivo `ADBMobileConfig.json` a fim de determinar se o local fornecido como parâmetro está dentro dos POIs. Se as coordenadas atuais estão dentro de um POI definido, uma variável de dados de contexto é preenchida e enviada com a chamada `trackLocation`.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackLocationWithLatLonData(lat, lon [, contextData]);
      ```

      * Retorna: N/A
      * Parâmetro: `lat`
         * Tipo: número
         * Latitude da localização.
      * Parâmetro: `lon`
         * Tipo: número
         * Longitude do local.
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
         * Tipo: número
         * Valor que será adicionado ao valor vitalício atual do usuário.
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
         * Tipo: String
         * Nome da ação cronometrada que está sendo iniciada.
      * Parâmetro: `contextData`
         * Tipo: objeto
         * Dados de contexto adicionais para esta ocorrência.
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.trackTimedActionStartData(‘level1’, {‘userId’:42423});
      ```


* **trackTimedActionUpdateData**

   Transmita dados para atualizar os dados de contexto associados a determinada ação.

   Os dados transmitidos são anexados aos dados existentes para determinada ação e, se a mesma chave já estiver definida para a ação, os dados são sobrescritos.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackTimedActionUpdateData(name [, contextData])
      ```

      * Retorna: N/A
      * Parâmetro: `name`
         * Tipo: String
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

   Se você fornecer uma função de retorno de chamada, poderá acessar os valores de tempo finais. Se nenhum retorno de chamada for fornecido, ou se o retorno de chamada retornar true, o SDK da Adobe enviará automaticamente uma ocorrência. Quando volta um “false” da chamada de retorno, a ocorrência de ação cronometrada é eliminada.

   * Esta é a sintaxe para este método:

      ```objective-c
      trackTimedActionEndJsLogic(name [, callback])
      ```

      * Retorna: N/A
      * Parâmetros: `name`
         * Tipo: String
         * Nome da ação cronometrada que está sendo encerrada
      * Parâmetro: `callback`
         * Tipo: `function(inAppDuration, totalDuration, data)`
         * Método de chamada de retorno que terá `inAppDuration` (número), `totalDuration` (número) e `data` (objeto de dados de contexto) em seus parâmetros.

            É possível eliminar o envio da ocorrência final pelo SDK, retornando `false` em sua função de chamada de retorno.
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
         * Nome da ação cronometrada cuja existência deve ser verificada.
   * Esta é a amostra de código para este método:


      ```objective-c
      var actionExists = ADBMobile.trackTimedActionExistsJs(‘level1’);
      ```


* **trackingIdentifier**

   Retorna o identificador de visitante gerado automaticamente.

   Esta é um identificador de visitante único específico do aplicativo gerado pelos servidores da Adobe. Se não for possível atingir a geração de servidores no momento, a ID será gerada usando a CFUUID da Apple. O valor é gerado na primeira inicialização e é armazenado e usado a partir desse ponto. Essa ID é preservada entre as atualizações do aplicativo, é salva e restaurada durante o processo padrão de backup do aplicativo e é removida quando o aplicativo é desinstalado.

   >[!TIP]
   >
   >Se seu aplicativo for atualizado do SDK 3.x da Experience Cloud para o 4.x, a ID anterior de visitante, personalizada ou gerada automaticamente, será recuperada e armazenada como o identificador personalizado do usuário. Isso preserva os dados dos visitantes entre as atualizações de SDK. Para novas instalações no SDK 4.x, o identificador do usuário é `nil` e o identificador de rastreamento é usado. Para obter mais informações, consulte a linha userIdentifier abaixo.

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


## Métodos do Audience Manager {#section_0155C4DF04644EDAAF6159C420A158DE}

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
         * Tipo: função (perfil)
         * O perfil retornou do Audience Manager no parâmetro para a função de retorno de chamada.
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
      * Parâmetro: nenhum
   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMobile.audienceReset();
      ```


## Métodos do serviço de ID {#section_BEB6DA612EA4423FB354B65ECC941335}

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

   Além da Experience Cloud ID, você pode definir IDs de cliente adicionais para serem associados a cada visitante. A API de visitante aceita várias IDs do cliente para o mesmo visitante, juntamente com um identificador de tipo de cliente para separar o escopo de diferentes IDs do cliente. Este método corresponde a setCustomerIDs na biblioteca do JavaScript.

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
         * Tipo: ADBMobileVisitorAuthenticationState
Estado de autenticação do usuário. Os valores possíveis incluem:
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
