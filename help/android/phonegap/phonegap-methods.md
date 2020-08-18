---
description: É possível usar os métodos de plug-in do iOS PhoneGap para executar várias tarefas.
keywords: android;library;mobile;sdk
seo-description: É possível usar os métodos de plug-in do iOS PhoneGap para executar várias tarefas.
seo-title: Métodos do plug-in PhoneGap
solution: Marketing Cloud,Analytics
title: Métodos do plug-in PhoneGap
topic: Developer and implementation
uuid: bc3db9ce-81b7-45ec-88aa-6020c1db5d9c
translation-type: ht
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: ht
source-wordcount: '1569'
ht-degree: 100%

---


# Métodos do plug-in PhoneGap {#phonegap-plug-in-methods}

Os métodos do plug-in PhoneGap no Android podem ser usados para desempenhar uma variedade de tarefas.

Nos arquivos `html` em que deseja usar o rastreamento, adicione o código a seguir na guia `<head>`:

```js
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Métodos de configuração {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   Retorna o status de privacidade do usuário atual.

   Estes são os status disponíveis:

   * `ADB.optedIn`: Essas ocorrências são enviadas imediatamente.
   * `ADB.optedOut`: Essas ocorrências são descartadas.
   * `ADB.optUnknown`: Se o conjunto de relatórios **estiver** habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o conjunto de relatórios **não tiver** carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

      O valor padrão está definido no arquivo `ADBMobileConfig.json`.

   * Esta é a amostra de código para este método:

      ```java
      getPrivacyStatus(function (value) { myTempVal = value; }, function () {myTempVal = null;}); 
      ```

* **setPrivacyStatus**

   Define o de privacidade do usuário atual como `status` status.

   Você pode definir um dos seguintes estados:

   * `ADB.optedIn`: Essas ocorrências são enviadas imediatamente.
   * `ADB.optedOut`: Essas ocorrências são descartadas.
   * `ADB.optUnknown`: Se o conjunto de relatórios **estiver** habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o conjunto de relatórios **não tiver** carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

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

   Ativa (`true`) ou desativa (`false`) na exibição de informações de depuração. Por padrão, essa variável é `false`.

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

   Esta é uma ID de visitante exclusiva e específica do aplicativo gerada quando ele é iniciado pela primeira vez e é armazenada e usada a partir desse ponto. Essa ID é preservada entre as atualizações do aplicativo e é removida quando o aplicativo é desinstalado.

   >[!TIP]
   >
   >Se o aplicativo for atualizado do Experience Cloud 3.x para o 4.x SDK, a ID de visitante anterior (personalizada ou gerada automaticamente) será recuperada e armazenada como o identificador de usuário personalizado. Para obter mais informações, consulte `getUserIdentifier` abaixo. Esta ID preserva os dados de visitante entre atualizações do SDK.

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
   >Chamar `keepLifecycleSessionAlive` impede que seu aplicativo inicie uma nova sessão na próxima vez que for retomado a partir do segundo plano. Você só deve usar esse método se o seu aplicativo se registrar para notificações em segundo plano.

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
   >Tenha cuidado ao limpar a fila manualmente, pois o resultado não pode ser revertido.

   * Esta é a amostra de código para este método:

      ```js
      ADB.trackingClearQueue(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

## Métodos PII {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

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


## Métodos de rastreamento {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   Rastreia os cliques em deep links da Adobe.

   >[!TIP]
   >
   >Se a chamada de Ciclo de vida for um evento de inicialização, os dados do Adobe Link serão anexados, caso contrário, uma chamada extra será enviada.

   * Esta é a sintaxe para este método:

      ```js
      ADB.trackAdobeDeepLink(deeplinkURL, success, fail); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function (value) { alert('success'); },function (value) { alert('fail') }); 
      ```

* **trackState**

   Rastreia um estado de aplicativo com dados de contexto opcionais. Os estados são as exibições disponíveis no aplicativo, como `home dashboard`, `app settings`, `cart`, e assim por diante. Esses estados são semelhantes às páginas em um site, e as chamadas de `trackState` aumentam as visualizações de página.

   `cData`: objeto JSON com pares de valor chave para enviar em dados de contexto.

   * Esta é a sintaxe para este método:

      ```js
      ADB.trackState(string stateName[,JSON cData]);
      ```

   * Estas são amostras de código para este método:

      ```js
        ADB.trackState("login&amp;nbsp;page"); 
      ```

      ```js
        ADB.trackState("login page", {"user":"john","remember":"true"});
      ```

* **trackAction**

   Rastreia uma ação no seu aplicativo. As ações incluem `logins`, `banner taps`, `feed subscriptions` e outras métricas que ocorrem no aplicativo e que você deseja medir.

   * Esta é a sintaxe para este método:

      ```js
      ADB.trackAction(string action[,JSON cData]); 
      ```

   * Estas são as amostras de código para este método:

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

   Inicia uma ação programada com o nome `action`.

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

   Passa em `cData` para atualizar os dados de contexto associados a `action`>.

   Os `cData` passados estão anexados aos dados existentes da ação e, se a mesma chave já estiver definida como `action`, eles substituirão os dados.

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

## Métodos de sinal {#section_F9500D6BD95348E08E283C02B657019D}

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

   Processa uma solicitação de serviço do `Target`.

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

   Processa uma solicitação de serviço do `Target`.

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

## Métodos de aquisição {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   Envia uma solicitação ao servidor do Target configurado e retorna o valor da cadeia de caracteres da oferta.

   * Esta é a sintaxe para este método:

      ```java
      ADB.acquisitionCampaignStartForApp(appId, data, success, fail); 
      ```

   * Estas são as amostras de código para este método:

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’});  
      ```

## Identificador de publicidade {#section_194607D101B047A19C51B19E176E1500}

Na atividade principal gerada pelo Cordova, faça uma chamada `Config.submitAdvertisingIdentifierTask()` no método `onResume()`. Para obter mais informações, consulte [Métodos de configuração](/help/android/configuration/methods.md).

## Métodos do Audience Manager {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

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

   * Estas são as amostras de código para este método:

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

   * Estas são as amostras de código para este método:

      ```java
       ADB.audienceSignalWithData(function() {}, function() {} {‘key1’: ’value1’ ‘key2’: ‘value2’}); 
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’: ’value1’, ‘key2’:‘value2’}); 
      ```

* **audienceReset**

   Redefine o UUID do Audience Manager e limpa o perfil de visitante atual.

   * Esta é a amostra de código para este método:

      ```java
      ADB.audienceReset();
      ```

## Métodos do serviço de ID {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   Retorna a Experience Cloud ID do Serviço de ID.

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

   * Estas são as amostras de código para este método:

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’: ‘value_id_1’});  
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   Sincroniza os identificadores fornecidos ao serviço de ID.

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

   Retorna todas as `visitorID` que foram sincronizadas.

   * Esta é a sintaxe para este método:

      ```java
      ADB.visitorGetIDs (success, fail);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.visitorGetIDs(function (value) { alert(value); },function (value) { alert('fail') ;}); 
      ```
