---
description: É possível usar os métodos de plug-in do iOS PhoneGap para executar uma variedade de tarefas.
keywords: phonegap
seo-description: É possível usar os métodos de plug-in do iOS PhoneGap para executar uma variedade de tarefas.
seo-title: Métodos do plug-in PhoneGap
solution: Marketing Cloud,Analytics
title: Métodos do plug-in PhoneGap
topic: Desenvolvedor e implementação
uuid: bd830fe5-804a-4d0a-bb6-99a6d8da6a03
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# PhoneGap plug-in methods {#phonegap-plug-in-methods}

É possível usar os métodos de plug-in do iOS PhoneGap para executar várias tarefas.

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuration methods {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   Retorna o status de privacidade do usuário atual. Estes são os status disponíveis:

   * `ADB.optedIn`, em que as ocorrências são enviadas imediatamente.
   * `ADB.optedOut`, onde as ocorrências são descartadas.
   * `ADB.optUnknown`Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). **** Se o conjunto de relatórios **não tiver** carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.\
      O valor padrão está definido no arquivo `ADBMobileConfig.json`.

      * Esta é a amostra de código para este método:

         ```javascript
         getPrivacyStatus(function (value){myTempVal = value;},function(){myTempVal = null;});
         ```

* **setPrivacyStatus**

   Define o de privacidade do usuário atual como `status`status. Você pode definir um dos seguintes estados:
   * `ADB.optedIn`, em que as ocorrências são enviadas imediatamente.
   * `ADB.optedOut`, onde as ocorrências são descartadas.
   * `ADB.optUnknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas).****

      Se o conjunto de relatórios **não tiver** carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

   * Esta é a amostra de código para este método:

      ```javascript
        ADB.setPrivacyStatus('ADB.optedIn'); 
      ```

* **getLifetimeValue**

   Retorna o valor do tempo de vida do usuário atual. O valor padrão é 0.

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.getLifetimeValue(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```

* **setDebugLogging**

   Enables (`true`) or disables (`false`) viewing debug information. Por padrão, essa variável é `false`.

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   Obtém a versão da biblioteca.

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.getVersion(function(value){versionNum = value;},function(){versionNum=1.0;}); 
      ```

* **trackingIdentifier**

   Retorna o identificador de visitante gerado automaticamente. Esta é uma ID de visitante único e específica do aplicativo, gerada quando o aplicativo é inicializado e é armazenada e usada deste ponto em diante. Essa ID é preservada entre as atualizações de aplicativos e é removida quando o aplicativo é desinstalado.

   >[!TIP]
   >
   >If your app upgrades from the Experience Cloud 3.x to 4.x SDK, the previous visitor ID (custom or automatically generated) is retrieved and stored as the custom user identifier (see `getUserIdentifier` below). Isso preserva os dados do visitante entre as atualizações de SDK. For new installations on the 4.x SDK, the user identifier is `null`, and tracking identifier is used.

   * Esta é a amostra de código para este método:

      ```javascript
       ADB.trackingIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **getUserIdentifier**

   Retorna o identificador do usuário personalizado se algum identificador personalizado estiver configurado e retorna `null` se nenhum estiver configurado. O valor padrão é `null`.

   * Esta é a amostra de código para este método:

      ```javascript
      getUserIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **setUserIdentifier**

   Define o identificador do usuário para `identifier`.

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   Define o token do dispositivo para notificações por push.

   * Esta é a sintaxe para este método:

      ```javascript
      ADB.setPushIdentifier(pushIdentifier,success,fail);
      ```

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.setPushIdentifier('test_push_identifier',function(value){alert('success');},function(value){alert('fail');
      ```

* **keepLifecycleSessionAlive**

   Define a preferência manter vivo da sessão de ciclo de vida.

   >[!IMPORTANT]
   >
   >Calling `keepLifecycleSessionAlive` prevents your app from launching a new session the next time it is resumed from background. Você só deve usar esse método se o seu aplicativo se registrar para notificações em segundo plano.

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **trackingSendQueuedHits**

   Força a biblioteca a enviar todas as ocorrências na fila, independentemente das opções de agrupamento atuais.

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   Obtém ou define o número de chamadas de rastreamento armazenadas na fila offline.

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.trackingGetQueueSize(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **trackingClearQueue**

   Remove todo o número de chamadas de rastreamento armazenadas da fila offline.

   >[!CAUTION]
   >
   >Cuidado ao limpar a fila manualmente; o resultado não pode ser revertido.

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.trackingClearQueue(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **keepLifecycleSessionAlive**

   Indica ao SDK que o próximo resumo em segundo plano não deve iniciar uma nova sessão, independentemente do tempo limite de valor da sessão do ciclo de vida presente no arquivo de configuração.

   >[!IMPORTANT]
   >
   >Importante: este método é destinado a aplicativos que realizam registros para receber notificações enquanto são executados em segundo plano e só deve ser chamado a partir do código executado enquanto o aplicativo está funcionando em segundo plano.

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **collectLifecycleData**

   Indica ao SDK que os dados do ciclo de vida devem ser coletados para uso em todas as soluções no SDK. Para obter mais informações, consulte [Lifecycle metrics](/help/ios/metrics.md).

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.collectLifecycleData(); 
      ```


## PII methods {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   Envia uma solicitação de coleta de PII.

   * Esta é a sintaxe para este método:

      ```javascript
      ADB.collectPII(piiData,success,fail); 
      ```

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success'); },function (value) { alert('fail'); });
      ```

## Tracking methods {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   Rastreia os cliques em deep links da Adobe.

   >[!TIP]
   >
   >If the Lifecycle call is a launch event, the Adobe Link data will be appended, otherwise an extra call will be sent.

   * Esta é a sintaxe para este método:

      ```javascript
      ADB.trackAdobeDeepLink(deeplinkURL,success,fail);
      ```

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackPushMessageClickthrough**

   Rastreia um clique na mensagem por push.

   * Esta é a sintaxe para este método:

      ```javascrpt
      ADB.trackPushMessageClickthrough(userInfo,success,fail); 
      ```

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.trackPushMessageClickthrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackLocalNotificationClickThrough**

   Rastreia um clique na mensagem de notificação local.

   * Esta é a sintaxe para este método:

      ```javascript
      ADB.trackLocalNotificationClickThrough(userInfo,success,fail); 
      ```

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.trackLocalNotificationClickThrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackState**

   Rastreia um estado de aplicativo com dados de contexto opcionais. States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. Esses estados são semelhantes às páginas em um site e as chamadas de `trackState` aumentam as exibições de página. cData is a JSON object with key-value pairs to send in context data.

   * Esta é a sintaxe para este método:

      ```javascript
      ADB.trackState(stringstateName[,JSONcData]); 
      ```

   * Here are the code samples for this method:

      ```javascript
      ADB.trackState("loginpage");
      ```

      ```javascript
        ADB.trackState("loginpage",{"user":"john","remember":"true"});
      ```

* **trackAction**

   Rastreia uma ação no seu aplicativo. Actions are the things that happen in your app that you want to measure, include `logins`, `banner taps`, `feed subscriptions` and other metrics.

   * Esta é a sintaxe para este método:

      ```javascript
      ADB.trackAction(stringaction[,JSONcData]);
      ```

   * Estas são as amostras de código para este método:

      ```javascript
      ADB.trackAction("login");
      ```

      ```javascript
      ADB.trackAction("login",{"user":"john","remember":"true"})
      ```

* **trackActionFromBackground**

   Rastreia uma ação que ocorreu em segundo plano. Isso impede que os eventos do ciclo de vida sejam acionados em cenários específicos.

   * Esta é a sintaxe para este método:

      ```javascript
      ADB.trackActionFromBackground(stringaction[,JSONcData]); 
      ```

   * Estas são as amostras de código para este método:

      ```javascript
      ADB.trackActionFromBackground("login");
      ```

      ```javascript
      ADB.trackActionFromBackground("login",{"user":"john","remember":"true"});
      ```

* **trackLocation**

   Envia as coordenadas x e y atuais. Also uses the points of interest that were defined in the `ADBMobileConfig.json` file to determine if the location provided as a parameter is within any of your POIs. Se as coordenadas atuais estão dentro de um POI definido, uma variável de dados de contexto é preenchida e enviada com a chamada `trackLocation`.

   * Esta é a sintaxe para este método:

      ```javascript
       ADB.trackLocation(x,y[,JSONcData]);
      ```

   * Esta é a amostra de código para este método:

      ```javascript
      ADB.trackLocation('40.431596','-111.893713');
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Adiciona uma `amount` ao valor do ciclo de vida do usuário.

   * Esta é a sintaxe para este método:

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSONcData]);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.trackLifetimeValueIncrease('10.01');
      ```

* **trackTimed&#x200B;ActionStart**

   Inicia uma ação programada com a `action` de nome. Se você chamar este método para uma ação já iniciada, a ação programada anterior será substituída.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```java
      ADB.trackTimedActionStart(action[,JSONcData]);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   Transmite `cData` para atualizar os dados de contexto associados à `action`. The `cData` passed in is appended to the existing data for the given action, and overwrites the data if the same key is already defined for `action`.

   >[!TIP]
   >
   >Essa chamada não envia uma ocorrência.

   * Esta é a sintaxe para este método:

      ```java
      ADB.trackTimedActionUpdate(Stringaction[,JSONcData]);
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

   Retorna se uma ação programada está em andamento ou não.

   * Esta é a sintaxe para este método:

      ```java
      ADB.trackingTimedActionExists(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```


## Métodos do Target {#section_C45D2FE54AE04EB5BD24D3508F8A3212}

* **targetLoadRequest**

   Envia a solicitação para o servidor do `Target` configurado e retorna o valor da cadeia de caracteres da oferta.

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetLoadRequest(success,fail,name,defaultContent,parameters); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.targetLoadRequest(function (value)
      {myTempVal = value;},function() {myTempVal = null;},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   Envia uma solicitação para o servidor Target configurado.

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetLoadOrderConfirmRequest(success,fail,name,orderId,orderTotal,productPurchaseId,parameters); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.targetLoadRequest(function(value){myTempVal=value;}
      ,function()
      {myTempVal = null; }
      ,'name','orderId','total','purchaseId'
      ,{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   Limpa os cookies do Target do armazenamento compartilhado de cookies.

   * Esta é a amostra de código para este método:

      ```java
      ADB.targetClearCookies();
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Processa uma solicitação de serviço do Target.

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(success,fail,name,defaultContent,profileParameters,orderParameters,mboxParameters,requestLocationParameters
      ); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(function(){alert('success');},function(){alert('fail');},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadRequestWithName**

   Processa uma solicitação de serviço do Target.

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
      ADB.targetSessionID(success,fail); 
      ```

   * Esta é a amostra de código para este método:

      ```java
        ADB.targetSessionID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

* **targetPcID**

   Obtém o valor do cookie `PcID` retornado para este visitante pelo servidor Target.

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetPcID(success,fail);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.targetPcID(function(value){alert(value);},function(value){alert('fail');});
      ```

* **targetSetThirdPartyID**

   Define a ID de visitante personalizada para o Target.

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID,success,fail); 
      ```

   * Esta é a amostra de código para este grupo:

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **targetThirdPartyID**

   Obtém a ID de visitante personalizada para o Target.

   * Esta é a sintaxe para este método:

      ```java
      ADB.targetThirdPartyID(success,fail); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.targetThirdPartyID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

## Acquisition methods {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   Permite aos desenvolvedores iniciar uma campanha de aquisição de aplicativo como se o usuário tivesse clicado em um link. Isso é útil para criar links de aquisição manuais e gerenciar o redirecionamento da loja de aplicativos por conta própria (como com um `SKStoreView`).

   * Esta é a sintaxe para este método:

      ```java
      ADB.acquisitionCampaignStartForApp(appId,data,success,fail); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.acquisitionCampaignStartForApp('0652024f-adcd-49f9-9bd7-2552a4564d2f',{'extraDataKey':'extraDataValue'},success,fail); 
      ```


## Advertising identifier {#section_194607D101B047A19C51B19E176E1500}

In the `AppDelegate` generated by Cordova, call `[ADBMobile setAdvertisingIdentifier:]` in the `application:didFinishLaunchingWithOptions:` delegate method. For more information, see Configuration Methods.[](/help/ios/configuration/sdk-methods.md)

## Audience Manager methods {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   Obtém o perfil do visitante.

   * Esta é a sintaxe para este método:

      ```java
      ADB.audienceGetVisitorProfile();
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.audienceGetVisitorProfile(function(value){profile = value;},function(){profile = null;}); 
      ```

* **audienceGetDpuuid**

   Retorna DPUUID.

   * Esta é a sintaxe para este método:

      ```java
      ADB.audienceGetDpuuid(success,fail);
      ```

   * Esta é a amostra de código para este método:

      ```java
       ADB.audienceGetDpuuid(function(value){dpuuid=value;},function(){dpuuid=null;}); 
      ```

* **audienceGetDpid**

   Retorna DPID.

   * Esta é a sintaxe para este método:

      ```java
       ADB.audienceGetDpid(success,fail);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;},function(){dpid = null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   Define a DPID e a DPUUID.

   * Esta é a sintaxe para este método:

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid,dpuuid,success,fail);
      ```

   * Estas são as amostras de código para este método:

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’,function(){…},function(){…});
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’);
      ```

* **audienceSignalWithData**

   Processa uma solicitação de serviço do Audience Manager.

   * Esta é a sintaxe para este método:

      ```java
      ADB.audienceSignalWithData(success,fail,data);
      ```

   * Estas são as amostras de código para este método:

      ```java
      ADB.audienceSignalWithData(function(){},function(){},{‘key1’:’value1’,‘key2’:‘value2’});
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’:’value1’,‘key2’:‘value2’}); 
      ```

* **audienceReset**

   Redefine a UUID do Audience Manager e limpa o perfil de visitante atual.

   * Esta é a amostra de código para este método:

      ```java
      ADB.audienceReset(); 
      ```

## ID Service methods {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   Retorna a Experience Cloud ID a partir do serviço de ID.

   * Esta é a sintaxe para este método:

      ```java
      ADB.visitorGetMarketingCloudId(success,fail);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.visitorGetMarketingCloudId(function(value){mcid=value;},function(){mcid=null;}); 
      ```

* **visitorSyncIdentifiers**

   Sincroniza os identificadores fornecidos com o serviço de ID.

   * Esta é a sintaxe para este método:

      ```java
      ADB.visitorSyncIdentifiers(identifiers,success,fail);
      ```

   * Estas são as amostras de código para este método:

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’},function(){…},function(){…})) 
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:‘value_id_1’});
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   Sincroniza os identificadores fornecidos ao serviço de ID do visitante.

   * Esta é a sintaxe para este método:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState(identifiers,authenticationState,success,fail); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'},ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');});
      ```

* **visitorSyncIdentifierWithType**

   Sincroniza o identificador fornecido ao serviço de ID do visitante.

   * Esta é a sintaxe para este método:

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType,identifier,authenticationState,success,fail); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type','test-identifier',ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **visitorAppendToURL**

   Adiciona identificadores de visitantes ao URL fornecido.

   * Esta é a sintaxe para este método:

      ```java
      ADB.visitorAppendToURL(urlToAppend,success,fail);
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.visitorAppendToURL('test_visitor_url',function(value){alert(value);},'');
      ```

* **visitorGetIDs**

   Retorna todas as `visitorIDs` que foram sincronizadas.

   * Esta é a sintaxe para este método:

      ```java
      ADB.visitorGetIDs(success,fail)
      ```

   * Esta é a amostra de código para este método:

      ```java
      ADB.visitorGetIDs(function(value){alert(value);},function(value){alert('fail');}); 
      ```

