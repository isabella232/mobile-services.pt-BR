---
description: Informações para ajudá-lo a usar o arquivo de Configuração JSON do ADBMobile.
seo-description: Informações para ajudá-lo a usar o arquivo de Configuração JSON do ADBMobile.
seo-title: Configuração do ADBMobileConfig.json
solution: Experience Cloud,Analytics
title: Configuração do ADBMobileConfig.json
topic-fix: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
exl-id: 57d50d30-651c-4943-835e-1cbce7467baf
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 45%

---

# Arquivo de configuração ADBMobileConfig.json {#adbmobileconfig-json-config}

Informações para ajudá-lo a usar o arquivo de Configuração JSON do ADBMobile.

Atualmente, o SDK é compatível com várias soluções da Adobe Experience Cloud, incluindo o Analytics, o Target e o Audience Manager. Os métodos apresentam prefixos de acordo com a solução. Métodos de configuração recebem o prefixo &quot;Configuração&quot;.

* **rsids**

   (**Exigido pelo Analytics**) Um ou mais conjuntos de relatórios que receberão dados do Analytics. Várias IDs de conjunto de relatórios devem ser separadas por vírgulas, sem espaços entre elas.

   * Esta é a sintaxe para este método:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Exigido pelo Analytics e pelo Gerenciamento de público-alvo**). Servidor do Analytics ou do Gerenciamento de público-alvo, com base no nó principal. Essa variável deve ser preenchida com o domínio do servidor, sem um prefixo de protocolo `"https://"` ou `"https://"`. O prefixo do protocolo é manipulado automaticamente pela biblioteca com base na variável `ssl` .

   Se `ssl` for `true`, é realizada uma conexão segura com o servidor. Se `ssl` for `false`, é realizada uma conexão insegura com o servidor.

* **charset**

   Define o conjunto de caracteres que está sendo usado nos dados enviados para o Analytics. O charset é usado para converter dados recebidos em UTF-8 para fins de armazenamento e relatórios. Para obter mais informações, consulte [s.charSet](https://docs.adobe.com/content/help/pt-BR/analytics/implementation/vars/config-vars/charset.html).

* **ssl**

   Ativa (`true`) ou desativa (`false`) o envio de dados de medição via SSL (`HTTPS`). O valor padrão é `false`.

* **offlineEnabled**

   Quando ativado (`true`), as ocorrências são enfileiradas enquanto o dispositivo está offline e enviadas posteriormente quando o dispositivo está online. Seu conjunto de relatórios deve ter o carimbo de data e hora habilitado para usar o rastreamento offline.

   Se os carimbos de data e hora estiverem ativados em seu conjunto de relatórios, sua propriedade de configuração `offlineEnabled`deverá&#x200B;*ser `true`.* Caso o conjunto de relatórios não tenha um carimbo de data e hora, sua propriedade de configuração `offlineEnabled` *deve* ser `false`.

   Se isso não for configurado corretamente, os dados serão perdidos. Se não tiver certeza se um conjunto de relatórios tem um carimbo de data e hora, entre em contato com o Atendimento ao cliente. Caso esteja relatando dados AppMeasurement para um conjunto de relatórios que também coleta dados JavaScript, pode ser necessário configurar um conjunto de relatórios separado para dados móveis ou incluir um carimbo de data e hora personalizado em todas as ocorrências de JavaScript que usam a variável `s.timestamp` .

   O valor padrão é `false`.

* **lifecycleTimeout**

   Especifica o tempo, em segundos, que deve decorrer entre o momento em que o aplicativo é iniciado, mas antes que a inicialização seja considerada uma nova sessão. Esse tempo limite também se aplica quando o aplicativo é enviado para o plano de fundo e reativado. O tempo que o aplicativo gasta em segundo plano não é incluído na duração da sessão.

   O valor padrão é de 300 segundos.

* **batchLimit**

   Envie ocorrências em lotes.

   Por exemplo, se definido como `50`, as ocorrências são enfileiradas até que 50 sejam armazenadas, então todas as ocorrências em fila são enviadas. Requer `offlineEnabled=true` e o valor padrão é `0` (Sem agrupamento).

* **privacyDefault**

   As opções são:

   * `optedin` - as ocorrências são enviadas imediatamente.
   * `optedout` - as ocorrências serão descartadas.
   * `optunknown` - Se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (e então as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas). Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

      Isso define somente o valor padrão. Se esse valor for definido ou alterado no código, o valor definido pelo código será salvo no armazenamento local e será usado a partir de agora, até que seja alterado ou o aplicativo seja desinstalado e depois reinstalado.

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

   (**Exigido pelo Target**) Seu código de cliente atribuído.

* **timeout**

   Determina quanto tempo o target aguarda uma resposta.

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
