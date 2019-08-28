---
description: Informações para ajudá-lo a usar o arquivo de configurações JSON do ADBMobile.
seo-description: Informações para ajudá-lo a usar o arquivo de configurações JSON do ADBMobile.
seo-title: Configuração adbmobileconfig. json
solution: Marketing Cloud, Analytics
title: Configuração adbmobileconfig. json
topic: Desenvolvedor e implementação
uuid: cbcb 54 a 3-4 b 8 f -4651-8 ce 9-2731 ac 988545
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Arquivo de configuração adbmobileconfig. json {#adbmobileconfig-json-config}

Informações para ajudá-lo a usar o arquivo de configurações JSON do ADBMobile.

O SDK atualmente é compatível com diversas Soluções da Adobe Experience Cloud, incluindo Analytics, Target e Audience Manager. Os métodos apresentam prefixos de acordo com a solução. Métodos de configuração recebem o prefixo “Config”.

* **rsids**

   (**Required by Analytics**) One or more report suites to receive Analytics data. Diversas IDs de conjunto de relatórios devem ser separadas por vírgulas, sem espaçamento entre as mesmas.

   * Esta é a sintaxe para este método:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Exigido pelo Analytics e pelo Gerenciamento de público-alvo**). O servidor do Analytics ou do Gerenciamento de público-alvo, com base no nó principal. This variable should be populated with the server domain, without an `"https://"` or `"https://"` protocol prefix. O prefixo de protocolo é manipulado automaticamente pela biblioteca com base na variável `ssl`.

   Se `ssl` for `true`, é realizada uma conexão segura com o servidor. Se `ssl` for `false`, é realizada uma conexão insegura com o servidor.

* **charset**

   Define o conjunto de caracteres que está sendo usado nos dados enviados para o Analytics. O charset é usado para converter dados recebidos em UTF-8 para fins de armazenamento e relatórios. Para obter mais informações, consulte [s. charset](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (`HTTPS`). O valor padrão é `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. Seu conjunto de relatórios deve ter o carimbo de data e hora habilitado para usar o rastreamento offline.

   If time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. Caso o conjunto de relatórios não tenha um carimbo de data e hora, sua propriedade de configuração `offlineEnabled` *deve* ser `false`.

   Se isso não for configurado corretamente, os dados serão perdidos. Se não tiver certeza se um conjunto de relatórios tem carimbo de data e hora, entre em contato com o Atendimento ao cliente. If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   O valor padrão é `false`.

* **lifecycleTimeout**

   Especifica a duração, em segundos, entre as inicializações do aplicativo antes que a inicialização seja considerada uma nova sessão. Esse tempo de espera também se aplica quando seu aplicativo é enviado para segundo plano e reativado. O tempo que seu aplicativo gasta em segundo plano não está incluído na duração da sessão.

   O valor padrão é 300 segundos.

* **batchLimit**

   Envia as ocorrências em lotes.

   For example, if set to `50`, hits are queued until 50 are stored, then all queued hits are sent. Requer `offlineEnabled=true`, e o valor padrão é `0` (Sem lotes).

* **privacyDefault**

   As opções são:

   * `optedin` - as ocorrências são enviadas imediatamente.
   * `optedout` - as ocorrências serão descartadas.
   * `optunknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para opt-in (as ocorrências são enviadas) ou opt-out (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

      Isso define apenas o valor padrão. Se este valor for definido ou alterado no código, então o valor definido pelo código é salvo no armazenamento local e é usado dali em diante até que seja alterado ou o aplicativo seja desinstalado e depois reinstalado.

      O valor padrão é `optedin`.

* **poi**

   Cada matriz de POI contém o nome do POI, a latitude, a longitude e o raio (em metros) para a área do ponto. O nome do POI pode ser qualquer cadeia de caracteres. Quando uma chamada `trackLocation` é enviada, se as coordenadas atuais estão dentro de um POI definido, uma variável de dados de contexto é preenchida e enviada com a chamada `trackLocation`.

   * Esta é a amostra de código para esta variável:

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**Required by Target**) Your assigned client code.

* **timeout**

   Determina quanto tempo o Target aguarda por uma resposta.

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
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000],
                    ["santa cruz",36.972935,-122.01725,600]
                ]
    },
 "target" : {
  "clientCode" : "myTargetClientCode",
  "timeout" : 1
 },
 "audienceManager" : {
  "server" : "myServer.demdex.com"
 }
}
```
