---
description: Classes e métodos fornecidos pela biblioteca do BlackBerry.
title: Referência de classe e método do Adobe Mobile
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
exl-id: ad73ec1d-d082-4237-b7cb-b8ec2f7595a3
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 60%

---

# Referência de classe e método do Adobe Mobile {#adobe-mobile-class-and-method-reference}

Classes e métodos fornecidos pela biblioteca do BlackBerry.

O SDK oferece suporte atualmente ao Adobe Analytics e os métodos estão em classes separadas com base na solução .

## Configurações do SDK {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   Retorna a representação de enumeração do status de privacidade do usuário atual.

   * ADBMobilePrivacyStatusOptIn - as ocorrências são enviadas imediatamente.
   * ADBMobilePrivacyStatusOptOut - as ocorrências são descartadas.
   * ADBMobilePrivacyStatusUnknown - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (e então as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

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
   * `ADBMobilePrivacyStatusUnknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (e então as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

   * Esta é a sintaxe para este método:

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   Retorna o identificador do usuário se algum identificador personalizado estiver configurado. Retorna `null` se um identificador personalizado não estiver definido. O valor padrão é `null`.

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

   Rastreia um estado de aplicativo com dados de contexto opcionais. Os estados são as exibições disponíveis no aplicativo, como &quot;painel inicial&quot;, &quot;configurações do aplicativo&quot;, &quot;carrinho&quot; e assim por diante. Esses estados são semelhantes às páginas em um site, e as chamadas de `trackState` aumentam as visualizações de página.

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

   Rastreia uma ação no seu aplicativo. As ações são coisas que ocorrem no seu aplicativo e que deseja medir, como &quot;logons&quot;, &quot;toques em banners&quot;, &quot;assinaturas de feed&quot; e outras métricas.

   * Esta é a sintaxe para este método:

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Esta é a amostra de código para este método:

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   Envia as coordenadas x e y atuais. Substitua o evento pelo evento recebido do assinante para o BPS.

   * Esta é a sintaxe para este método:

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * Esta é a amostra de código para este método:

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` referência do arquivo de configuração {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

O arquivo `ADBMobileConfig.json` deve ser colocado na pasta *assets*.

* **rsids**

   (Obrigatório) Um ou mais conjuntos de relatórios que receberão dados do Analytics. Várias IDs de conjunto de relatórios devem ser separadas por vírgulas, sem espaços entre elas.

   Esta é a amostra de código para esta variável:

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (Obrigatório). Servidor do Analytics. Essa variável deve ser preenchida com o domínio do servidor, sem um prefixo de protocolo `https://` ou `https://`. O prefixo do protocolo é manipulado automaticamente pela biblioteca com base na variável `ssl` . Se `ssl` for `true`, é realizada uma conexão segura com o servidor. Se `ssl` for `false`, é realizada uma conexão insegura com o servidor.

* **charset**

   Define o conjunto de caracteres que está sendo usado nos dados enviados para o Analytics. O charset é usado para converter dados recebidos em UTF-8 para fins de armazenamento e relatórios.

* **ssl**

   Ativa (`true`) ou desativa (`false`) o envio de dados de medição via SSL (HTTPS). O valor padrão é `false`.

* **offlineEnabled**

   Quando ativado (`true`), as ocorrências são enfileiradas enquanto o dispositivo está offline e enviadas posteriormente quando o dispositivo está online. Seu conjunto de relatórios deve ter o carimbo de data e hora habilitado para usar o rastreamento offline.

   >[!TIP]
   >
   >Se os carimbos de data e hora estiverem ativados no conjunto de relatórios, sua propriedade de configuração `offlineEnabled` *deverá* ser `true`. Caso o conjunto de relatórios não tenha um carimbo de data e hora, sua propriedade de configuração `offlineEnabled` *deve* ser false. Se isso não for configurado corretamente, os dados serão perdidos. Se você não tem certeza se um conjunto de relatórios tem um carimbo de data e hora,   entre em contato com o   [Suporte Enterprise](https://helpx.adobe.com/br/contact/enterprise-support.ec.html).

   Caso esteja relatando dados AppMeasurement para um conjunto de relatórios que também coleta dados JavaScript, pode ser necessário configurar um conjunto de relatórios separado para dados móveis, ou incluir um carimbo de data e hora personalizado em todas as ocorrências de JavaScript usando a variável `s.timestamp` .

   O valor padrão é `false`.

* **lifecycleTimeout**

   Especifica o tempo, em segundos, que deve decorrer entre o momento em que o aplicativo é iniciado, mas antes que a inicialização seja considerada uma nova sessão. Esse tempo limite também se aplica quando o aplicativo é enviado para o plano de fundo e reativado. O tempo que o aplicativo gasta em segundo plano não é incluído na duração da sessão.

   O valor padrão é de 300 segundos.

* **batchLimit**

   Número máximo de ocorrências offline armazenadas na fila. O valor padrão é 0 (sem limite).

* **privacyDefault**

   * `optedin` - as ocorrências são enviadas imediatamente.
   * `optedout` - as ocorrências serão descartadas.
   * `optunknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (e então as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas).

      Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.
   Essa variável define somente o valor inicial. Se esse valor for definido ou alterado no código, o novo valor será usado a partir de então até que seja alterado, ou quando o aplicativo for desinstalado e instalado novamente.

   O valor padrão é `optedin`.

Este é um exemplo de um arquivo `ADBMobileConfig.json`:

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
