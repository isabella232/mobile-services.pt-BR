---
description: Esta informação ajuda a usar o arquivo de configuração ADBMobile.json.
seo-description: Esta informação ajuda a usar o arquivo de configuração ADBMobile.json.
seo-title: Configuração JSON do ADBMobile
solution: Experience Cloud,Analytics
title: Configuração JSON do ADBMobile
topic: Developer and implementation
uuid: d9708d59-e30a-4f6c-ab1b-d9499855d0c2
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '1715'
ht-degree: 100%

---


# Configuração JSON do ADBMobile {#adbmobile-json-config}

Esta informação ajuda a usar o arquivo de configuração `ADBMobile.json`.

## Referência do arquivo de configuração do ADBMobileConfig.json {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

O mesmo arquivo de configuração pode ser usado para seu aplicativo em várias plataformas:

>[!TIP]
>
>No **iOS**, o arquivo `ADBMobileConfig.json` pode ser colocado em qualquer lugar acessível no seu pacote.

* **aquisição**

   Ativa a aquisição de aplicativos móveis.

   Se esta seção estiver faltando, habilite a aquisição do aplicativo móvel e baixe o arquivo de configuração do SDK novamente. Para obter mais informações, consulte *referrerTimeout* abaixo.

   * `server` - Servidor de aquisição que está marcado na primeira inicialização para um referenciador de aquisição.
   * `appid` - ID gerada que identifica de forma exclusiva este aplicativo no servidor de aquisição.
   * Versão mínima do SDK: 4.1

* **analyticsForwardingEnabled**

   As propriedades no objeto `audienceManager`. Se o `Audience Manager` estiver configurado e `analyticsForwardingEnabled` estiver definido como `true`, todo o tráfego do Analytics também será encaminhado ao Audience Manager. O valor padrão é `false`.

   * Versão mínima do SDK: 4.8.0

* **backdateSessionInfo**

   Ativa/desativa a capacidade do Adobe SDK de colocar data retroativa em ocorrências de informações de sessão.

   As ocorrências de informações da sessão consistem em falhas e duração da sessão e podem ser ativadas ou desativadas.

   * Se você definir o valor como `false`, as ocorrências são **desabilitadas**.

      O SDK retorna ao comportamento anterior ao 4.1 de agregar as informações da sessão anterior com a primeira ocorrência da sessão subsequente. O Adobe SDK também anexa as informações da sessão ao ciclo de vida atual, evitando a criação de uma visita inflada. Como as visitas infladas não são mais criadas, ocorre uma queda imediata na contagem de visitas.

   * Se você não fornecer um valor, o valor padrão é `true` e as ocorrências são **habilitadas**.

      Quando as ocorrências são ativadas, o Adobe SDK atualiza a ocorrência de informações da sessão para 1 segundo após a ocorrência final na sessão anterior. Isso significa que os dados de falha e sessão estarão correlacionados com a data correta em que ocorreram. Um efeito colateral é que o SDK pode criar uma visita para a ocorrência retroativa. Uma ocorrência recebe data retroativa em cada nova inicialização do aplicativo.

   * Versão mínima do SDK: 4.6
   >[!IMPORTANT]
   >
   >As informações de ocorrência de sessão retroativa são enviadas em uma chamada de servidor da sessão de informações e podem ser aplicadas chamadas de servidor adicionais.


* **batchLimit**

   Limite de números de ocorrências que serão enviadas em chamadas consecutivas. Por exemplo, se o `batchLimit` for definido como 10, cada ocorrência antes da 10ª será armazenada na fila. Quando a 10ª ocorrência entrar, todas as 10 ocorrências serão enviadas na ordem.

   * O valor padrão é `0`, o que significa que o agrupamento não está ativado.
   * Exige `offlineEnabled = true`.
   * Versão mínima do SDK: 4.1

* **charset**

   Define o conjunto de caracteres que está sendo usado nos dados enviados para o Analytics. O charset é usado para converter dados recebidos em UTF-8 para fins de armazenamento e relatórios. Para obter mais informações, consulte [s.charSet](https://docs.adobe.com/content/help/pt-BR/analytics/implementation/vars/config-vars/charset.html).

   * Versão mínima do SDK: 4.0

* **clientCode**

   O código de cliente atribuído.

   >[!IMPORTANT]
   >
   >Esta variável é exigida pelo Target.

   * Versão mínima do SDK: 4.0

* **coopUnsafe**

   Para membros do Device Co-op que requerem que esse valor seja definido como `true`, é necessário trabalhar com a equipe do Co-op para solicitar um sinalizador de lista de bloqueios em sua conta do Device Co-op. Não há um caminho de autoatendimento para habilitar esses sinalizadores.

   Lembre-se das seguintes informações:

   * Quando `coopUnsafe` estiver definido como `true`, `coop_unsafe=1` sempre será anexado a ocorrências do Audience Manager e da ID do visitante.
   * Se você habilitar o encaminhamento pelo lado do servidor do Analytics para o Audience Manager, você também verá `coop_unsafe=1` em ocorrências do Analytics.

   Estas são algumas informações adicionais:

   * Versão mínima do SDK: 4.16.1
   * A propriedade booleana do objeto `marketingCloud` que, quando definido como `true`, causa a remoção do dispositivo do Device Co-op da Experience Cloud.
   * O valor padrão é `false`.
   * Essa configuração é usada **somente** para clientes provisionados do Device Co-op.



* **environmentId**

   A ID do ambiente que você deseja utilizar. Você pode especificar uma ID válida (`environmentId=8`), e se `environmentId` não for incluída, o ambiente padrão Produção é usado.

   * Versão mínima do SDK: 4.14

* **lifecycleTimeout**

   O valor padrão é de 300 segundos.

   Especifica o tempo, em segundos, que deve decorrer entre o momento em que o aplicativo é iniciado, mas antes que a inicialização seja considerada uma nova sessão. Esse tempo limite também se aplica quando o aplicativo é enviado para o plano de fundo e reativado. O tempo que o aplicativo gasta em segundo plano não é incluído na duração da sessão.

   * Versão mínima do SDK: 4.0

* **messages**

   Gerado automaticamente pelo Adobe Mobile Services, define as configurações para as mensagens no aplicativo. Para obter mais informações, consulte a seção *Descrição das mensagens* abaixo.

   * Versão mínima do SDK: 4.2

* **offlineEnabled**

   Quando ativado, as ocorrências são enfileiradas enquanto o dispositivo está offline e enviadas posteriormente quando o dispositivo estiver online. Seu conjunto de relatórios deve ter o carimbo de data e hora habilitado para usar o rastreamento offline. O valor padrão é `false`.

   Estas são algumas informações importantes:

   * Se o carimbo de data e hora estiver ativado no conjunto de relatórios, sua propriedade de configuração `offlineEnabled` *deve* ser verdadeira.
   * Caso o conjunto de relatórios não tenha um carimbo de data e hora, sua propriedade de configuração `offlineEnabled` *deve* ser false.

      Se isso não for configurado corretamente, os dados serão perdidos. Se você não tem certeza se um conjunto de relatórios tem um carimbo de data e hora,   entre em contato com o   Atendimento ao Cliente ou baixe o arquivo de configuração em Adobe Mobile Services. Caso esteja relatando dados AppMeasurement para um conjunto de relatórios que também coleta dados JavaScript, pode ser necessário configurar um conjunto de relatórios separado para dados móveis, a fim de evitar a perda de dados, ou incluir um carimbo de data e hora personalizado nas ocorrências de JavaScript que usam a variável `s.timestamp`.

   * Versão mínima do SDK: 4.0

* **org**

   Especifica a ID da organização da Experience Cloud para o Adobe Experience Platform Identity Service.

   * Versão mínima do SDK: 4.3

* **poi**

   Cada matriz de POI contém o nome do POI, a latitude, a longitude e o raio (em metros) para a área do ponto. O nome do POI pode ser qualquer cadeia de caracteres. Quando uma chamada `trackLocation` é enviada, se as coordenadas atuais estiverem em um POI definido, uma variável de dados de contexto será preenchida e enviada com a chamada `trackLocation`.

   * Versão mínima do SDK: 4.0

   ```js
   "poi" [ 
           ["sanfrancisco",37.757144,-122.44812,7000]
           ["santacruz",36.972935,-122.01725,600]
         ] 
   ```

   >[!TIP]
   >
   >A partir da versão 4.2, os POIs são definidos na interface do Adobe Mobile e sincronizados dinamicamente no arquivo de configuração do aplicativo. Esta sincronização exige a configuração `analytics.poi`:

   ```js
   “analytics.poi”: “`https://assets.adobedtm.com/…/yourfile.json`”,
   ```

   Se esta configuração não estiver definida, o arquivo `ADBMobile.json` deve ser atualizado para incluir esta linha. Para baixar um arquivo de configuração atualizado, consulte [Antes de começar](/help/ios/getting-started/requirements.md).

* **postback**

   A definição para o modelo de mensagem &quot;callback&quot; é mostrada abaixo:

   ```js
   "payload":{
       "templateurl":"",//required- will be token-expanded prior to being sent
       "templatebody":"", //optional-if this length > 0 POST will be used as transport method. This is a base-64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"", //optional-if this is length > 0 and POST type is selected, this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout": 0 //optional-number of seconds to wait before timingout.Defaultis2.}
   ```

   O objeto `payload` no código é um exemplo de carga para uma definição de mensagem no arquivo `ADBMobileConfig.json`. Para obter mais informações, consulte [Postbacks](/help/ios/analytics-main/postback/postback.md).

   * Versão mínima do SDK: 4.6

* **privacyDefault**

   * Para `optedin`, as ocorrências são enviadas imediatamente.
   * Para `optedout`, as ocorrências são descartadas.
   * Para `optunknown`, se o conjunto de relatórios estiver habilitado para mostrar o carimbo de data e hora, as ocorrências serão salvas até o status de privacidade ser alterado para aceitar (as ocorrências são enviadas) ou rejeitar (as ocorrências são descartadas).

      Se o conjunto de relatórios não tiver carimbo de hora e data, as ocorrências são descartadas até o status de privacidade ser alterado para opt in.

      Isso só define o valor inicial. Se este valor estiver definido ou alterado no código, o novo valor é usado até que seja alterado novamente, ou quando o aplicativo é desinstalado e instalado novamente. O valor padrão é `optedin`.

   * Versão mínima do SDK: 4.0

* **referrerTimeout**

   Número de segundos que o SDK aguarda os dados do referenciador de aquisição no lançamento inicial antes de atingir o tempo limite. Se você estiver usando a aquisição, recomendamos um tempo limite de 5 segundos.

   >[!IMPORTANT]
   >
   >Esta variável é exigida pela Aquisição. Se a variável estiver definida como `0` ou não estiver incluída, o SDK não aguardará os dados de aquisição e as métricas de aquisição não serão rastreadas.

   * Versão mínima do SDK: 4.1

* **remotes**

   Configurado automaticamente e define os terminais hospedados pela Adobe para arquivos de configuração dinâmicos. O último tempo de atualização de cada arquivo de configuração é verificado em relação à versão atual em cada inicialização e as atualizações são baixadas e salvas.

   * `analytics.poi` é o terminal para a configuração de POI hospedada.

   * `messages` é o terminal para a configuração da mensagem hospedada no aplicativo.

   * Versão mínima do SDK: 4.2

* **rsids**

   Um ou mais conjuntos de relatórios para receber dados do Analytics. Várias IDs de conjunto de relatórios devem ser separadas por vírgulas, sem espaços entre elas.

   ```js
   "rsids": "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2" 
   ```

   >[!IMPORTANT]
   >
   >Esta variável é exigida pelo Analytics.

   * Versão mínima do SDK: 4.0

* **server**

   O servidor Analytics ou Gerenciamento de público-alvo, com base no nó principal.

   Essa variável deve ser preenchida com o domínio do servidor, sem um prefixo de protocolo `https://` ou `https://`. Este prefixo é manipulado automaticamente pela biblioteca com base na variável `ssl`.

   Se `ssl` for `true`, é realizada uma conexão segura com o servidor. Se `ssl` for `false`, é realizada uma conexão insegura com o servidor.

   >[!IMPORTANT]
   >
   >Esta variável é exigida pelo Analytics e/ou pelo Gerenciamento de público-alvo.

   * Versão mínima do SDK: 4.0

* **ssl**

   >[!IMPORTANT]
   >
   > A partir da versão 4.10.0, o padrão SSL será true, se o sinalizador não estiver definido.

   Ativa (`true`) ou desativa (`false`) a capacidade de enviar dados de medição por SSL (HTTPS).

   A definição para o modelo de mensagem &quot;callback&quot; é mostrada abaixo:

   ```js
   "payload":{
       "templateurl":"",//required-will be token-expanded prior to being sent
       "templatebody":"",//optional-if this length > 0, POST will be used as transport method. This is a base64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"",//optional-if this is length > 0 and POST type is selected this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout":0//optional-numberofsecondstowaitbeforetimingout.Defaultis2.} 
   ```

   O objeto `payload` no código é uma amostra de carga para uma definição de mensagem que consta no arquivo `ADBMobileConfig.json`. Para obter mais informações, consulte [Postbacks](/help/ios/analytics-main/postback/postback.md).

   * Versão mínima do SDK: 4.0

* **timeout**

   Determina quanto tempo o Target aguarda uma resposta.

   * Versão mínima do SDK: 4.0


## Exemplo de arquivo `ADBMobileConfig.json` {#section_52FA7C71A99147AFA9BE08D2177D8DA7}

A seguir, há um exemplo de arquivo `ADBMobileConfig.json`:

```js
{ 
    "version": "2014-08-05T19:18:28.169Z", 
    "marketingCloud" : { 
        "org": "016D5C175213CCA80A490D05@AdobeOrg", 
        "coopUnsafe": false 
    }, 
    "target": { 
        "clientCode": "", 
        "timeout": 5, 
        "environmentId": 8 
    }, 
    "audienceManager": { 
        "server": "", 
        "analyticsForwardingEnabled": false 
    }, 
    "acquisition": { 
        "server": "c00.adobe.com", 
        "appid": "10a77a60192fbb628376e1b1daeeb65debf934e2c807e067ceb2963a41b165ee" 
    }, 
    "analytics": { 
        "rsids": "coolApp", 
        "server": "my.CoolApp.com", 
        "ssl": true, 
        "offlineEnabled": true, 
        "charset": "UTF-8", 
        "lifecycleTimeout": 300, 
        "privacyDefault": "optedin", 
        "batchLimit": 0, 
        "referrerTimeout": 5, 
        "poi": [ 
            ["san francisco",37.757144,-122.44812,7000],  
            ["santa cruz",36.972935,-122.01725,600] 
        ] 
    }, 
    "messages": [ 
        { 
            "messageId": "cb426565-a563-497a-a889-9dbeb451f8ae", 
            "template": "fullscreen", 
            "payload": { 
                 "html": "<!DOCTYPE html><html><head><meta charset=\"utf-8\" /><title></title><style></style></head><body><iframe src=\"https://www.adobe.com/\" frameborder=\"0\"></iframe></body></html>"
            },
            "showOffline": false,
            "showRule": "always",
            "endDate": 2524730400,
            "startDate": 0,
            "audiences": [],
            "triggers": [
                {
                    "key": "pev2",
                    "matches": "eq",
                    "values": [
                        "AMACTION:custom"
                    ] 
                } 
            ] 
        } 
    ], 
    "remotes": {
        "analytics.poi": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0faadc2f9ed92bc00003b.json",
        "messages": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0f9e2c2f9ed92bc000032.json"
    }
}
```

## Descrição das mensagens {#section_B97D654BA92149CE91F525268D7AD71F}

O nó de mensagens é gerado automaticamente pelo Adobe Mobile Services e geralmente não precisa ser alterado manualmente. A descrição a seguir é fornecida para fins de solução de problemas:

* &quot;messageId&quot;

   * ID gerada, obrigatória

* &quot;modelo&quot;

   * &quot;alerta&quot;, &quot;tela cheia&quot; ou &quot;local&quot;
   * obrigatório

* &quot;carga&quot;

   * &quot;html&quot;

      * apenas modelo de tela cheia, obrigatório
      * html definindo a mensagem
   * &quot;imagem&quot;

      * apenas tela cheia, opcional
      * url para a imagem que será usada para uma imagem em tela cheia
   * &quot;altImage&quot;

      * apenas tela cheia, opcional
      * nome da imagem agrupada que será usada se o url especificado em
         `image` está inatingível
   * &quot;título&quot;

      * tela cheia e alerta, obrigatório
      * texto de título para uma tela cheia ou mensagem de alerta
   * &quot;conteúdo&quot;

      * alerta e notificação local, obrigatório
      * subtexto para uma mensagem de alerta ou texto de notificação para uma mensagem de notificação local
   * &quot;confirmar&quot;

      * alerta, opcional
      * texto usado no botão confirmar
   * &quot;cancelar&quot;

      * alerta, obrigatório
      * texto usado no botão cancelar
   * &quot;url&quot;

      * alerta, opcional
      * ação de url que será carregada se o botão confirmar for clicado
   * &quot;aguardar&quot;

      * notificação local, obrigatório
      * quantidade de tempo de espera (em segundos) para postar a notificação local depois de corresponder aos seus critérios









* &quot;showOffline&quot;

   * verdadeiro ou falso
   * o padrão é falso

* &quot;showRule&quot;

   * &quot;sempre&quot;, &quot;uma vez&quot; ou &quot;untilClick&quot;
   * obrigatório

* &quot;endDate&quot;

   * número de segundos desde 1° de janeiro de 1970
   * o padrão é 2524730400

* &quot;startDate&quot;

   * número de segundos desde 1° de janeiro de 1970
   * o padrão é 0

* &quot;audiences&quot;

   Uma matriz de objetos que define como a mensagem deve ser mostrada:

   * &quot;key&quot;

      Nome da variável a ser procurada na ocorrência, e é obrigatório.

   * &quot;matches&quot;

      Tipo de correspondência usado ao fazer a comparação:

      * eq = igual
      * ne = não é igual
      * co = contém
      * nc = não contém
      * sw = inicia com
      * ew = termina com
      * ex = existe
      * nx = não existe
      * lt = menor que
      * le = menor que ou igual
      * gt = maior que
      * ge = maior que ou igual
   * &quot;values&quot;

      Uma matriz de valores usada para corresponder com o valor da variável nomeada no seguinte:

      * key
      * com o tipo de correspondência em
      * matches


* &quot;triggers&quot;

   O mesmo que audiences, mas aqui são as ações em vez do público-alvo:

   * &quot;key&quot;
   * &quot;matches&quot;
   * &quot;values&quot;
