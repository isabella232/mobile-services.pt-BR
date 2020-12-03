---
description: Classes e métodos fornecidos pela biblioteca do BlackBerry.
seo-description: Classes e métodos fornecidos pela biblioteca do BlackBerry.
seo-title: Referência de classe e método do Adobe Mobile
title: Referência de classe e método do Adobe Mobile
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 59%

---


# Referência de classe e método do Adobe Mobile {#adobe-mobile-class-and-method-reference}

Classes e métodos fornecidos pela biblioteca do BlackBerry.

Atualmente, o SDK oferece suporte ao Adobe Analytics e os métodos estão em classes separadas com base na solução.

## Configurações do SDK {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   Retorna a representação de enumeração do status de privacidade do usuário atual.

   * ADBMobilePrivacyStatusOptIn - as ocorrências são enviadas imediatamente.
   * ADBMobilePrivacyStatusOptOut - as ocorrências são descartadas.
   * ADBMobilePrivacyStatusUnknown - se o conjunto de relatórios tiver um carimbo de data e hora, as ocorrências serão salvas até que o status de privacidade seja alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

      O valor padrão está definido no arquivo `ADBMobileConfig.json`.

   * Esta é a sintaxe para este método:

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* **setPrivacyStatus**

   Define o de privacidade do usuário atual como `status` status. É definido como um dos valores abaixo:

   * `ADBMobilePrivacyStatusOptIn` - as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut` - as ocorrências serão descartadas.
   * `ADBMobilePrivacyStatusUnknown` - Se o conjunto de relatórios tiver um carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

   * Esta é a sintaxe para este método:

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   Retorna o identificador do usuário se algum identificador personalizado estiver configurado. Returns `null` if a custom identifier is not set. O valor padrão é `null`.

   * Esta é a sintaxe para este método:

      ```cpp
      static QString getUserIdentifier();
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      QString userId = ADBMobile::getUserIdentifier(); 
      ```

* **setUserIdentifier**

   Define o identificador do usuário para `identifier`.

   * Esta é a sintaxe para este método:

      ```cpp
      static void setUserIdentifier(QString identifier);
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      ADBMobile::setUserIdentifier("billybob");
      ```

* **getDebugLogging**

   Retorna a preferência de log para a depuração atual. O valor padrão é `false`.

   * Esta é a sintaxe para este método:

      ```cpp
      static bool getDebugLogging();
      ```

   * Esta é a amostra de código para este método:

      ```cpp
       bool debugging = ADBMobile::getDebugLogging(); 
      ```

* **setDebugLogging**

   Define a preferência do log de depuração como `debugLogging`.

   * Esta é a sintaxe para este método:

      ```cpp
      static void setDebugLogging(bool debugLogging);
      ```

   * Esta é a amostra de código para este método:

      ```cpp
        ADBMobile::setDebugLogging(true); 
      ```

* **collectLifecycleData**

   Indica ao SDK que os dados do ciclo de vida devem ser coletados para uso em todas as soluções no SDK. Para obter mais informações, consulte [Medições de ciclo de vida](/help/blackberry/metrics.md).

   * Esta é a sintaxe para este método:

      ```cpp
      static void collectLifecycleData();
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      ApplicationUI::ApplicationUI(bb::cascades::Application *app):  QObject(app)  { 
      //... 
      ADBMobile::collectLifecycleData(); 
      }
      ```

## Métodos do Analytics {#section_91F4AD0A045D4E4E8F9A93450503E49E}

Cada um desses métodos é usado para enviar dados para seu conjunto de relatórios do Adobe Analytics.

* **trackState**

   Rastreia um estado de aplicativo com dados de contexto opcionais. Os estados são as visualizações que estão disponíveis no aplicativo, como &quot;painel inicial&quot;, &quot;configurações do aplicativo&quot;, &quot;carrinho&quot; e assim por diante. Esses estados são semelhantes às páginas em um site, e as chamadas de `trackState` aumentam as visualizações de página.

   >[!TIP]
   >
   >Esta é a única chamada de rastreamento que aumenta as exibições de página.

   * Esta é a sintaxe para este método:

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Esta é a amostra de código para este método:

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   Rastreia uma ação no seu aplicativo. As ações são coisas que ocorrem no aplicativo e que você deseja avaliar, como &quot;logons&quot;, &quot;toques em banners&quot;, &quot;subscrições de feed&quot; e outras métricas.

   * Esta é a sintaxe para este método:

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Esta é a amostra de código para este método:

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   Envia as coordenadas x e y atuais. Substitua o evento pelo evento recebido do assinante para BPS.

   * Esta é a sintaxe para este método:

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * Esta é a amostra de código para este método:

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` referência do arquivo de configuração {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

The `ADBMobileConfig.json` file must be placed in the *assets* folder.

* **rsids**

   (Obrigatório) Um ou mais conjuntos de relatórios para receber dados do Analytics. Várias IDs de conjunto de relatórios devem ser separadas por vírgulas, sem espaços entre elas.

   Estas são as amostras de código para esta variável:

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (Obrigatório). Servidor do Analytics. Essa variável deve ser preenchida com o domínio do servidor, sem um prefixo de protocolo `https://` ou `https://`. O prefixo do protocolo é manipulado automaticamente pela biblioteca com base na `ssl` variável. Se `ssl` for `true`, é realizada uma conexão segura com o servidor. Se `ssl` for `false`, é realizada uma conexão insegura com o servidor.

* **charset**

   Define o conjunto de caracteres que você está usando para os dados enviados ao Analytics. O charset é usado para converter dados recebidos em UTF-8 para fins de armazenamento e relatórios.

* **ssl**

   Ativa (`true`) ou desativa (`false`) o envio de dados de medição via SSL (HTTPS). O valor padrão é `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. Seu conjunto de relatórios deve ter o carimbo de data e hora habilitado para usar o rastreamento offline.

   >[!TIP]
   >
   >If timestamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. Caso o conjunto de relatórios não tenha um carimbo de data e hora, sua propriedade de configuração `offlineEnabled` *deve* ser false. Se isso não for configurado corretamente, os dados serão perdidos. Se você não tem certeza se um conjunto de relatórios tem um carimbo de data e hora,   entre em contato com o   [Suporte](https://helpx.adobe.com/br/contact/enterprise-support.ec.html)empresarial.

   If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data, or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   O valor padrão é `false`.

* **lifecycleTimeout**

   Especifica o tempo, em segundos, que deve decorrer entre o momento em que o aplicativo é iniciado, mas antes que a inicialização seja considerada uma nova sessão. Esse tempo limite também se aplica quando o aplicativo é enviado para o plano de fundo e reativado. O tempo que o aplicativo gasta em segundo plano não é incluído na duração da sessão.

   O valor padrão é de 300 segundos.

* **batchLimit**

   Número máximo de ocorrências offline armazenadas na fila. O valor padrão é 0 (Sem limite).

* **privacyDefault**

   * `optedin` - as ocorrências são enviadas imediatamente.
   * `optedout` - as ocorrências serão descartadas.
   * `optunknown` - Se o conjunto de relatórios tiver um carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas).

      Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.
   Essa variável define somente o valor inicial. Se esse valor for definido ou alterado no código, o novo valor será usado até que seja alterado, ou o aplicativo será desinstalado e reinstalado.

   O valor padrão é `optedin`.

The following is an example of an `ADBMobileConfig.json` file:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 5, 
        "privacyDefault" : "optedin", 
    } 
}
```
