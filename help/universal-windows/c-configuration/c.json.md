---
description: Informações para ajudá-lo a usar o arquivo de configuração JSON do ADBMobile.
seo-description: Informações para ajudá-lo a usar o arquivo de configuração JSON do ADBMobile.
seo-title: Configuração do ADBMobileConfig.json
solution: Experience Cloud,Analytics
title: Configuração do ADBMobileConfig.json
topic: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 41%

---


# ADBMobileConfig.json config file {#adbmobileconfig-json-config}

Informações para ajudá-lo a usar o arquivo de configuração JSON do ADBMobile.

O SDK suporta atualmente várias Soluções Adobe Experience Cloud, incluindo Analytics, Público alvo e Audience Manager. Os métodos apresentam prefixos de acordo com a solução. Métodos de configuração recebem o prefixo &quot;Config&quot;.

* **rsids**

   (**Exigido pelo Analytics**) Um ou mais conjuntos de relatórios para receber dados do Analytics. Várias IDs de conjunto de relatórios devem ser separadas por vírgulas, sem espaços entre elas.

   * Esta é a sintaxe para este método:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Exigido pelo Analytics e Gerenciamento** de Audiências). Servidor do Analytics ou Gerenciamento de Audiências, com base no nó pai. Essa variável deve ser preenchida com o domínio do servidor, sem um prefixo de protocolo `"https://"` ou `"https://"`. O prefixo do protocolo é manipulado automaticamente pela biblioteca com base na `ssl` variável.

   Se `ssl` for `true`, é realizada uma conexão segura com o servidor. Se `ssl` for `false`, é realizada uma conexão insegura com o servidor.

* **charset**

   Define o conjunto de caracteres que você está usando para os dados enviados ao Analytics. O charset é usado para converter dados recebidos em UTF-8 para fins de armazenamento e relatórios. Para obter mais informações, consulte [s.charSet](https://docs.adobe.com/content/help/pt-BR/analytics/implementation/vars/config-vars/charset.html).

* **ssl**

   Ativa (`true`) ou desativa (`false`) o envio de dados de medição via SSL (`HTTPS`). O valor padrão é `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. Seu conjunto de relatórios deve ter o carimbo de data e hora habilitado para usar o rastreamento offline.

   If time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. Caso o conjunto de relatórios não tenha um carimbo de data e hora, sua propriedade de configuração `offlineEnabled` *deve* ser `false`.

   Se isso não for configurado corretamente, os dados serão perdidos. Se não tiver certeza se um conjunto de relatórios tem carimbo de data e hora, entre em contato com o Atendimento ao cliente. If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   O valor padrão é `false`.

* **lifecycleTimeout**

   Especifica a duração, em segundos, entre as inicializações do aplicativo antes que a inicialização seja considerada uma nova sessão. Esse tempo limite também se aplica quando o aplicativo é enviado para o plano de fundo e reativado. O tempo que o aplicativo gasta em segundo plano não é incluído na duração da sessão.

   O valor padrão é de 300 segundos.

* **batchLimit**

   Envie ocorrências em lotes.

   Por exemplo, se definido como `50`, as ocorrências são enfileiradas até que 50 sejam armazenadas e todas as ocorrências em fila são enviadas. Exige `offlineEnabled=true`e o valor padrão é `0` (Sem agrupamento).

* **privacyDefault**

   As opções são:

   * `optedin` - as ocorrências são enviadas imediatamente.
   * `optedout` - as ocorrências serão descartadas.
   * `optunknown` - Se o conjunto de relatórios tiver um carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

      Isso define somente o valor padrão. Se esse valor for definido ou alterado no código, o valor definido pelo código será salvo no armazenamento local e será usado para frente até que seja alterado ou o aplicativo seja desinstalado e reinstalado.

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

   (**Exigido pelo Público alvo**) Seu código de cliente atribuído.

* **timeout**

   Determina quanto tempo o público alvo aguarda uma resposta.

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
