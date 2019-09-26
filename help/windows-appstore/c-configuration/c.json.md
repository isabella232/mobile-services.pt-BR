---
description: Informações para ajudá-lo a usar o arquivo de configurações JSON do ADBMobile.
seo-description: Informações para ajudá-lo a usar o arquivo de configurações JSON do ADBMobile.
seo-title: ADBMobileConfig.json config file
solution: Marketing Cloud,Analytics
title: ADBMobileConfig.json config file
topic: Desenvolvedor e implementação
uuid: a45b91cc-982e-4d6c-a4e4-d2e4b4fa7556
translation-type: tm+mt
source-git-commit: 1dbdb998228bd3b0ae41e774b6e9aa111d8dbe1c

---


# `ADBMobileConfig.json` config file {#adbmobileconfig-json-config}

Information to help you use the `ADBMobile.json` config file.

O SDK atualmente é compatível com diversas Soluções da Adobe Experience Cloud, incluindo Analytics, Target e Audience Manager. Os métodos apresentam prefixos de acordo com a solução. Métodos de configuração recebem o prefixo “Config”.

* **rsids**

   (Exigido pelo Analytics) Um ou mais conjuntos de relatórios que receberão dados do Analytics. Diversas IDs de conjunto de relatórios devem ser separadas por vírgulas, sem espaçamento entre as mesmas.

   * Here are the code samples for this variable:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (Exigido pelo Analytics e pelo Gerenciamento de público-alvo). O servidor do Analytics ou do Gerenciamento de público-alvo, com base no nó principal. This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. O prefixo de protocolo é manipulado automaticamente pela biblioteca com base na variável `ssl`.

   Se `ssl` for `true`, é realizada uma conexão segura com o servidor. Se `ssl` for `false`, é realizada uma conexão insegura com o servidor.

* **charset**

   Define o conjunto de caracteres que está sendo usado nos dados enviados para o Analytics. O charset é usado para converter dados recebidos em UTF-8 para fins de armazenamento e relatórios. For more information, see s.charSet.[](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html)

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). O valor padrão é `false`.

* **offlineEnabled**

   Quando habilitado (true), as ocorrências são enfileiradas enquanto o dispositivo estiver offline e enviadas posteriormente, quando o dispositivo estiver online. Seu conjunto de relatórios deve ter o carimbo de data e hora habilitado para usar o rastreamento offline.

   >[!IMPORTANT]
   >
   >IIf time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be true. Caso o conjunto de relatórios não tenha um carimbo de data e hora, sua propriedade de configuração `offlineEnabled` *deve* ser false. Se isso não for configurado corretamente, os dados serão perdidos. Se você não tem certeza se um conjunto de relatórios tem um carimbo de data e hora, entre em contato com Atendimento ao cliente. Caso esteja relatando dados AppMeasurement para um conjunto de relatórios que também coleta dados JavaScript, pode ser necessário configurar um conjunto de relatórios separado para dados de dispositivos móveis, ou incluir um carimbo de data e hora personalizado nas ocorrências de JavaScript que usam a variável `s.timestamp`.

* **lifecycleTimeout**

   Especifica a duração, em segundos, entre as inicializações do aplicativo antes que a inicialização seja considerada uma nova sessão. Esse tempo de espera também se aplica quando seu aplicativo é enviado para segundo plano e reativado. O tempo que seu aplicativo gasta em segundo plano não está incluído na duração da sessão. O valor padrão é 300 segundos.

* **batchLimit**

   Envia as ocorrências em lotes. Por exemplo, se definido como 50, as ocorrências são enfileiradas até que 50 estejam armazenadas, depois todas as ocorrências armazenadas são enviadas. Exige `offlineEnabled=true`. O valor padrão é `0` (Sem agrupamento).

* **privacyDefault**

   * `optedin` - as ocorrências são enviadas imediatamente.
   * `optedout` - as ocorrências serão descartadas.
   * `optunknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para opt-in (as ocorrências são enviadas) ou opt-out (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

      O valor padrão é `optedin`.

      >[!TIP]
      >
      >Isso define somente o valor padrão. Se este valor for definido ou alterado no código, então o valor definido pelo código é salvo no armazenamento local e é usado dali em diante até que seja alterado ou o aplicativo seja desinstalado e depois reinstalado.

* **poi**

   Cada matriz de POI contém o nome do POI, a latitude, a longitude e o raio (em metros) para a área do ponto. O nome do POI pode ser qualquer cadeia de caracteres. Quando uma chamada `trackLocation` é enviada, se as coordenadas atuais estão dentro de um POI definido, uma variável de dados de contexto é preenchida e enviada com a chamada `trackLocation`.

   * Esta é a amostra de código para esta variável:

      ```js
      "poi": [
                  ["san francisco",37.757144,-122.44812,7000], 
                  ["santa cruz",36.972935,-122.01725,600] 
              ]
      ```

* **clientCode**

   (**Required by Target**) Your assigned client code.

* **timeout**

   Determina quanto tempo o Target aguarda uma resposta.

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

