---
description: Classes e métodos fornecidos pela biblioteca do BlackBerry.
seo-description: Classes e métodos fornecidos pela biblioteca do BlackBerry.
seo-title: Referência de classe e método do Adobe Mobile
title: Referência de classe e método do Adobe Mobile
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Adobe Mobile class and method reference {#adobe-mobile-class-and-method-reference}

Classes e métodos fornecidos pela biblioteca do BlackBerry.

Atualmente, o SDK oferece suporte ao Adobe Analytics e os métodos estão em classes separadas com base na solução.

## SDK settings {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   Retorna a representação de enumeração do status de privacidade do usuário atual.

   * ADBMobilePrivacyStatusOptIn - as ocorrências são enviadas imediatamente.
   * ADBMobilePrivacyStatusOptOut - as ocorrências são descartadas.
   * ADBMobilePrivacyStatusUnknown - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para opt-in (as ocorrências são enviadas) ou opt-out (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

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

   Define o de privacidade do usuário atual como `status`status. É definido como um dos valores abaixo:

   * `ADBMobilePrivacyStatusOptIn` - as ocorrências são enviadas imediatamente.
   * `ADBMobilePrivacyStatusOptOut` - as ocorrências serão descartadas.
   * `ADBMobilePrivacyStatusUnknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para opt-in (as ocorrências são enviadas) ou opt-out (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

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

## Analytics methods {#section_91F4AD0A045D4E4E8F9A93450503E49E}

Cada um desses métodos é usado para enviar dados para seu conjunto de relatórios do Adobe Analytics.

* **trackState**

   Rastreia um estado de aplicativo com dados de contexto opcionais. Os estados são as visualizações que estão disponíveis no seu aplicativo, como “painel inicial”, “configurações do aplicativo”, “carrinho” e assim por diante. Esses estados são semelhantes às páginas em um site e as chamadas de `trackState` aumentam as exibições de página.

   >[!TIP]
   >
   >This is the only tracking call that increments page views.

   * Esta é a sintaxe para este método:

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Esta é a amostra de código para este método:

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   Rastreia uma ação no seu aplicativo. As ações são coisas que ocorrem no seu aplicativo e que deseja avaliar, como “logons”, “toques em banners”, “assinaturas de feed” e outras métricas.

   * Esta é a sintaxe para este método:

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Esta é a amostra de código para este método:

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   Envia as coordenadas x e y atuais. Substitua “event” pelo evento recebido do assinante para BPS.

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

   (Obrigatório) Um ou mais conjuntos de relatórios que receberão dados do Analytics. Diversas IDs de conjunto de relatórios devem ser separadas por vírgulas, sem espaçamento entre as mesmas.

   Estas são as amostras de código para esta variável:

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (Obrigatório). Servidor do Analytics. This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. O prefixo de protocolo é manipulado automaticamente pela biblioteca com base na variável `ssl`. Se `ssl` for `true`, é realizada uma conexão segura com o servidor. Se `ssl` for `false`, é realizada uma conexão insegura com o servidor.

* **charset**

   Define o conjunto de caracteres que está sendo usado nos dados enviados para o Analytics. O charset é usado para converter dados recebidos em UTF-8 para fins de armazenamento e relatórios.

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). O valor padrão é `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. Seu conjunto de relatórios deve ter o carimbo de data e hora habilitado para usar o rastreamento offline.

   >[!TIP]
   >
   >If timestamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. Caso o conjunto de relatórios não tenha um carimbo de data e hora, sua propriedade de configuração `offlineEnabled` *deve* ser false. Se isso não for configurado corretamente, os dados serão perdidos. Se você não tem certeza se um conjunto de relatórios tem um carimbo de data e hora, entre em contato com Suporte [empresarial](https://helpx.adobe.com/contact/enterprise-support.ec.html).

   Caso esteja relatando dados AppMeasurement para um conjunto de relatórios que também coleta dados JavaScript, pode ser necessário configurar um conjunto de relatórios separado para dados de dispositivos móveis, ou incluir um carimbo de data e hora personalizado nas ocorrências de JavaScript que usam a variável `s.timestamp`.

   O valor padrão é `false`.

* **lifecycleTimeout**

   Especifica a duração, em segundos, entre as inicializações do aplicativo antes que a inicialização seja considerada uma nova sessão. Esse tempo de espera também se aplica quando seu aplicativo é enviado para segundo plano e reativado. O tempo que seu aplicativo gasta em segundo plano não está incluído na duração da sessão.

   O valor padrão é 300 segundos.

* **batchLimit**

   O número máximo de ocorrências offline armazenada na fila. O valor padrão é 0 (Sem limite).

* **privacyDefault**

   * `optedin` - as ocorrências são enviadas imediatamente.
   * `optedout` - as ocorrências serão descartadas.
   * `optunknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para opt-in (as ocorrências são enviadas) ou opt-out (as ocorrências são descartadas).

      Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.
   Essa variável define somente o valor inicial. Se esse valor for definido ou alterado no código, o novo valor será usado até que seja alterado novamente, ou quando o aplicativo for desinstalado e instalado novamente.

   O valor padrão é `optedin`.

A seguir, um exemplo de um arquivo `ADBMobileConfig.json`:

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
