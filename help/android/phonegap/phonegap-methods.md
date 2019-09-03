---
description: É possível usar os métodos de plug-in do iOS PhoneGap para executar várias tarefas.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: É possível usar os métodos de plug-in do iOS PhoneGap para executar várias tarefas.
seo-title: Métodos de plug-in do phonegap
solution: Marketing Cloud, Analytics
title: Métodos de plug-in do phonegap
topic: Desenvolvedor e implementação
uuid: bc 3 db 9 ce -81 b 7-45 ec -88 aa -6020 c 1 db 5 d 9 c
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# PhoneGap plug-in methods{#phonegap-plug-in-methods}

Os métodos do plug-in PhoneGap no Android podem ser usados para desempenhar uma variedade de tarefas.

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```js
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuration methods {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   Retorna o status de privacidade do usuário atual.

   Estes são os status disponíveis:

   * `ADB.optedIn`: Essas ocorrências são enviadas imediatamente.
   * `ADB.optedOut`: Essas ocorrências são descartadas.
   * `ADB.optUnknown`: Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). **** Se o conjunto de relatórios **não tiver** carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

      O valor padrão está definido no arquivo `ADBMobileConfig.json`.

   * Esta é a amostra de código para este método:

      ```java
      getPrivacyStatus(function (value) { myTempVal = value; }, function () {myTempVal = null;}); 
      ```

* **setPrivacyStatus**

   Define o de privacidade do usuário atual como `status`status.

   Você pode definir um dos seguintes estados:

   * `ADB.optedIn`: Essas ocorrências são enviadas imediatamente.
   * `ADB.optedOut`: Essas ocorrências são descartadas.
   * `ADB.optUnknown`: Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). **** Se o conjunto de relatórios **não tiver** carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

   * Esta é a amostra de código para este método:

      ```java
      ADB.setPrivacyStatus('ADB.optedIn');
      ```

* **getLifetimeValue**

   Retorna o valor do tempo de vida do usuário atual. O valor padrão é 0.

   * Esta é a amostra de código para este método:

      ```java
      ADB.getLifetimeValue(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

* **setDebugLogging**

   Enables (`true`) or disables (`false`) viewing debug information. Por padrão, essa variável é `false`.

   * Esta é a amostra de código para este método:

      ```java
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   Obtém a versão da biblioteca.

   * Esta é a amostra de código para este método:

      ```java
      ADB.getVersion(function (value) { versionNum = value }, function () { versionNum = 1.0;});
      ```

* **trackingIdentifier**

   Retorna o identificador de visitante gerado automaticamente.

   Esta é uma ID de visitante único específica do aplicativo gerada no lançamento inicial e, em seguida, armazenada e utilizada a partir desse ponto. Esta ID é preservada entre as atualizações do aplicativo e é removida quando o aplicativo é desinstalado.

   >[!TIP]
   >
   >Se o aplicativo for atualizado do SDK 3. x da Experience Cloud para o 4. x, a ID de visitante anterior (personalizada ou gerada automaticamente) será recuperada e armazenada como o identificador do usuário personalizado. Para obter mais informações, consulte `getUserIdentifier` abaixo. Esta ID preserva os dados de visitante entre atualizações do SDK.

   Para novas instalações no SDK 4.x, o identificador do usuário é `null` e o identificador de rastreamento é usado.

   * Esta é a amostra de código para este método:

      ```java
      ADB.trackingIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

* **getUserIdentifier**

   Se um identificador de usuário do cliente foi definido, retorna esse identificador. Caso contrário, retorna `null`. O valor padrão é `null`.

   * Esta é a amostra de código para este método:

      ```java
      getUserIdentifier(function(value) { myTempVal = value; }, function () { myTempVal = null; });
      ```

* **setUserIdentifier**

   Define o identificador do usuário para `identifier`.

   * Esta é a amostra de código para este método:

      ```java
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   Define o token do dispositivo para notificações por push.

   ```java
   getUserIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; });
   ```

   * Esta é a sintaxe para este método:

      ```java
      ADB.setPushIdentifier(pushIdentifier, success, fail);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.setPushIdentifier('test_push_identifier',function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **keepLifecycleSessionAlive**

   Define a preferência manter vivo da sessão de ciclo de vida.

   >[!IMPORTANT]
   >
   >Calling `keepLifecycleSessionAlive` prevents your app from launching a new session the next time it is resumed from background. Você só deve usar esse método se o seu aplicativo se registrar para notificações em segundo plano.

   * Esta é a amostra de código para este método:

      ```js
      ADB.keepLifecycleSessionAlive(); 
      ```

* **trackingSendQueuedHits**

   Força a biblioteca a enviar todas as ocorrências na fila, independentemente das opções de agrupamento atuais.

   * Esta é a amostra de código para este método:

      ```js
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   Obtém ou define o número de chamadas de rastreamento armazenadas na fila offline.

   * Esta é a amostra de código para este método:

      ```js
      ADB.trackingGetQueueSize(function (value) { myTempVal = value;}, function () { myTempVal = null;}); 
      ```

* **trackingClearQueue**

   Remove todo o número de chamadas de rastreamento armazenadas da fila offline.

   >[!WARNING]
   >
   >Tenha cuidado ao limpar a fila manualmente, porque ela não pode ser revertida.

   * Esta é a amostra de código para este método:

      ```js
      ADB.trackingClearQueue(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

## PII methods {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   Envia uma solicitação de coleta de PII.

   * Esta é a sintaxe para este método:

   ```javascript
   ADB.collectPII(piiData,success, fail);
   ```

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success') },function (value) { alert('fail') ;});
      ```


## Tracking methods {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   Rastreia os cliques em deep links da Adobe.

   >[!TIP]
   >
   >Se a chamada de ciclo de vida for um evento de inicialização, os dados do Adobe Link serão anexados, caso contrário, uma chamada extra será enviada.

   * Esta é a sintaxe para este método:

      ```js
      ADB.trackAdobeDeepLink(deeplinkURL, success, fail); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function (value) { alert('success'); },function (value) { alert('fail') }); 
      ```

* **trackState**

   Rastreia um estado de aplicativo com dados de contexto opcionais. States are the views that are available in your app, such as such as `home dashboard`, `app settings`, `cart`, and so on. Esses estados são semelhantes às páginas em um site e as chamadas de `trackState` aumentam as exibições de página.

   `cData`: objeto JSON com pares de valor chave para enviar em dados de contexto.

   * Esta é a sintaxe para este método:

      ```js
      ADB.trackState(string stateName[,JSON cData]);
      ```

   * Aqui estão exemplos de código para este método:

      ```js
        ADB.trackState("login&amp;nbsp;page"); 
      ```

      ```js
        ADB.trackState("login page", {"user":"john","remember":"true"});
      ```

* **trackAction**

   Rastreia uma ação no seu aplicativo. Actions include `logins`, `banner taps`, `feed subscriptions`, and other metrics that occur in your app and that you want to measure.

   * Esta é a sintaxe para este método:

      ```js
      ADB.trackAction(string action[,JSON cData]); 
      ```

   * Aqui estão exemplos de código para este método:

      ```js
        ADB.trackAction("login");
      ```

      ```js
        ADB.trackAction("login", {"user":"john","remember":"true"}); 
      ```

* **trackLocation**

   Envia as coordenadas x e y atuais. Também usa pontos de interesse definidos no arquivo `ADBMobileConfig.json` a fim de determinar se o local fornecido como parâmetro está dentro do POI. Se as coordenadas atuais estão dentro de um POI definido, uma variável de dados de contexto é preenchida e enviada com a chamada `trackLocation`.

   * Esta é a sintaxe para este método:

      ```java
      ADB.trackLocation(x, y[,JSON cData]); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.trackLocation('40.431596', '-111.893713'); 
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Adiciona uma `amount` ao valor do ciclo de vida do usuário.

   * Esta é a sintaxe para este método:

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSON cData]); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.trackLifetimeValueIncrease('10.01'); 
      ```

* **trackTimed&#x200B;ActionStart**

   Start a timed action with the name `action`.

   Se você chamar este método para uma ação já iniciada, a ação programada anterior será substituída.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```java
      ADB.trackTimedActionStart(action[,JSON cData]);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   Pass in `cData` to update the context data that is associated with the `action`&gt;.

   The `cData` that is passed is appended to the existing data for the action and, if the same key is already defined for `action`, overwrites the data.

   * Esta é a sintaxe para este método:

      ```java
      ADB.trackTimedActionUpdate(String action[,JSON cData]);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.trackTimedActionUpdate("cartToCheckout",{'SampleContextDataKey3':'SampleContextDataVal3','SampleContextDataKey4':'SampleContextDataVal4'});
      ```

* **trackTimed&#x200B;ActionEnd**

   Encerra uma ação programada.

   * Esta é a amostra de código para este método:

      ```java
      ADB.trackTimedActionEnd("cartToCheckout"); 
      ```

* **trackingTimedActionExists**

   Retorna se uma ação cronometrada estiver em andamento.

   * Esta é a sintaxe para este método:

      ```java
      ADB.trackingTimedActionExists(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

## Beacon methods {#section_F9500D6BD95348E08E283C02B657019D}

* **trackBeacon**

   Rastreia quando um usuário está perto de um sinal.

   * Esta é a sintaxe para este método:

      ```js
      ADB.trackBeacon(uuid, major, minor, proximity, cData) 
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.trackBeacon('2F234454-CF6D-4A0F-ADF2-F4911BA9FFA6', 1, 2, 
      ADB.beaconUnknown, {'hp':'hp_val','hp.company':'adobe'}
      ```

* **clearCurrentBeacon**

   Apaga os dados de sinal depois que o usuário se distancia de um sinal.

   * Esta é a sintaxe para este método:

      ```js
      ADB.clearCurrentBeacon(success, fail)
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.clearCurrentBeacon(); 
      ```

## Métodos do Target {#section_8670140C5A3F455E887830AFFDF91D59}

* **targetLoadRequest**

   Envia uma solicitação ao servidor do `Target` configurado e retorna o valor da cadeia de caracteres da oferta.

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetLoadRequest(success, fail, name, defaultContent, parameters);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.targetLoadRequest(function&nbsp;(value)
      {myTempVal = value }, function () { myTempVal = null;},'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   Envia uma solicitação para o servidor `Target` configurado.

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetLoadOrderConfirmRequest(success, fail name orderId, orderTotal, productPurchaseId, parameters); 
      ```

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetLoadRequest(function (value) { myTempVal = value }
      , function ()
      { myTempVal = null; } 
      , 'name' 'orderId' 'total', 'purchaseId',
      {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   Limpa os cookies do `Target` do armazenamento compartilhado de cookies.

   * Esta é a amostra de código para este método:

      ```java
      ADB.targetClearCookies(); 
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Processes a `Target` service request.

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(
        success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters requestLocationParameters
        ); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters  (function () { alert('success'); }, function () { alert('fail'); }, ;'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}, {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'});
      ```

* **targetLoadRequestWithName**

   Processes a `Target` service request.

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetLoadRequestWithRequestName(success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.targetLoadRequestWithName(
      function (value){ // handle target success} ,
      function() { // handle target failure }, 
      "mboxName",
      "defaultContent",
      {"profileParameters":"profileParametervalues"}
      {"orderId" : "32FGJ4XK" , "orderTotal" : "123.33" , "purchasedProductIds":"[46,34]" }
      {"mboxParameters":"mboxParametersvalues"}
      );
      ```

* **targetSessionID**

   Obtém o valor do cookie `SessionID` retornado para este visitante pelo servidor Target.

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetSessionID (success, fail); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.targetSessionID(function (value) { alert(value) },function (value){ alert('fail'); });  
      ```

* **targetPcID**

   Obtém o valor do cookie `PcID` retornado para este visitante pelo servidor do `Target`.

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetPcID (success, fail); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.targetPcID(function  (value) { alert(value) },function (value) { alert('fail'); });
      ```

* **targetSetThirdPartyID**

   Define a ID de visitante personalizada para o Target.

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID, success, fail); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id' function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **targetThirdPartyID**

   Obtém a ID de visitante personalizada para o Target.

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetThirdPartyID(success, fail);
      ```

   * Esta é uma amostra de código para este método:

      ```java
       ADB.targetThirdPartyID(function (value) { alert(value); },function (value) { alert('fail')__;});
      ```

## Acquisition methods {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   Envia uma solicitação ao servidor do Target configurado e retorna o valor da cadeia de caracteres da oferta.

   * Esta é a sintaxe para este método:

      ```java
      ADB.acquisitionCampaignStartForApp(appId, data, success, fail); 
      ```

   * Aqui estão exemplos de código para este método:

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’});  
      ```

## Advertising identifier {#section_194607D101B047A19C51B19E176E1500}

In the main activity that is generated by Cordova, call `Config.submitAdvertisingIdentifierTask()` in the `onResume()` method. Para obter mais informações, consulte [Métodos de configuração](/help/android/configuration/methods.md).

## Audience Manager methods {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   Obtém o perfil do visitante.

   * Esta é a sintaxe para este método:

      ```java
      ADB.audienceGetVisitorProfile(); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.audienceGetVisitorProfile(function(value) { profile = value;}, function() { profile = null; }); 
      ```

* **audienceGetDpuuid**

   Retorna DPUUID.

   * Esta é a sintaxe para este método:

      ```java
      ADB.audienceGetDpuuid(success fail);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.audienceGetDpuuid(function(value) { dpuuid = value;}, function(){dpuuid = null; }); 
      ```

* **audienceGetDpid**

   Retorna DPID.

   * Esta é a sintaxe para este método:

      ```java
      ADB.audienceGetDpid(success, fail);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;}, function() {dpid =  null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   Define a DPID e a DPUUID.

   * Esta é a sintaxe para este método:

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid, dpuuid, success, fail); 
      ```

   * Aqui estão exemplos de código para este método:

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’, function() {…}, function(){…};
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’); 
      ```

* **audienceSignalWithData**

   Processa uma solicitação de serviço do Audience Manager.

   * Esta é a sintaxe para este método:

      ```java
      ADB.audienceSignalWithData(success, fail, data);
      ```

   * Aqui estão exemplos de código para este método:

      ```java
       ADB.audienceSignalWithData(function() {}, function() {} {‘key1’: ’value1’ ‘key2’: ‘value2’}); 
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’: ’value1’, ‘key2’:‘value2’}); 
      ```

* **audienceReset**

   UUID do Audience Manager e limpa o perfil de visitante atual.

   * Esta é a amostra de código para este método:

      ```java
      ADB.audienceReset();
      ```

## ID Service methods {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   Retorna a Experience Cloud ID pelo Serviço de ID.

   * Esta é a sintaxe para este método:

      ```java
      ADB.visitorGetMarketingCloudId(success, fail); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.visitorGetMarketingCloudId(function (value) { mcid = value;},function (){ mcid = null;});
      ```

* **visitorSyncIdentifiers**

   Sincroniza os identificadores fornecidos com o serviço de ID.

   * Esta é a sintaxe para este método:

      ```java
      ADB.visitorSyncIdentifiers(identifiers, success, fail); 
      ```

   * Aqui estão exemplos de código para este método:

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’: ‘value_id_1’});  
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   Sincroniza os identificadores fornecidos ao Serviço de ID.

   * Esta é a sintaxe para este método:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState
      (identifiers, authenticationState, success, fail); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'}, ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **visitorSyncIdentifierWithType**

   Sincroniza o identificador fornecido ao serviço de ID.

   * Esta é a sintaxe para este método:

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType, identifier authenticationState, success, fail); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type', 'test-identifier', ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success') },function (value) { alert('fail'); }); 
      ```

* **visitorAppendToURL**

   Adiciona identificadores de visitantes ao URL fornecido.

   * Esta é a sintaxe para este método:

      ```java
       ADB.visitorAppendToURL(urlToAppend, success, fail); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.visitorAppendToURL('test_visitor_url', function (value) alert(value);},'');
      ```

* **visitorGetIDs**

   Returns all `visitorID`s that have been synced.

   * Esta é a sintaxe para este método:

      ```java
      ADB.visitorGetIDs (success, fail);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.visitorGetIDs(function (value) { alert(value); },function (value) { alert('fail') ;}); 
      ```
