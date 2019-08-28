---
description: As instruções a seguir ajudam a redirecionar uma campanha de aquisição com um Link de marketing com base em uma impressão digital do dispositivo.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: As instruções a seguir ajudam a redirecionar uma campanha de aquisição com um Link de marketing com base em uma impressão digital do dispositivo.
seo-title: Testar a aquisição do link de marketing
solution: Marketing Cloud, Analytics
title: Testar a aquisição do link de marketing
topic: Desenvolvedor e implementação
uuid: 69503 e 01-182 d -44 c 6-b 0 fb-e 1 c 012 ffa 3 bd
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

As instruções a seguir ajudam a redirecionar uma campanha de aquisição com um Link de marketing com base em uma impressão digital do dispositivo.

1. Conclua as tarefas de pré-requisito na [Aquisição](/help/ios/acquisition-main/acquisition.md)de aplicativos móveis.
1. In the Adobe Mobile Services UI, click **[!UICONTROL Marketing Links Builder]** and generate an acquisition Marketing Link URL that sets the App Store as the destination for iOS devices.

   Por exemplo:

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   Para obter mais informações, consulte [Criador de links de marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).


1. Open the generated link on the iOS device and open `https://c00.adobe.com/v3/<appid>/end`.

   Você deve ver o contextData na resposta JSON:

   ```js{"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. Verifique se as seguintes configurações em seu arquivo de configuração estão corretas:

   | Configuração | Valor |
   |--- |--- |
   | aquisição | The server should be  `c00.adobe.com`. `appid` deve ser igual ao *`appid`* link de aquisição. |
   | analytics | `referrerTimeout` deve ter um valor maior que 0. |

1. (Condicional) Se a configuração SSL no arquivo de configuração do seu aplicativo for `false`, atualize seu link de aquisição para usar o protocolo HTTP em vez de HTTPS.
1. Clique no link gerado pelo dispositivo móvel no qual você deseja instalar o aplicativo.

   Os servidores da Adobe ( `c00.adobe.com` ) armazenam a impressão digital e redirecionam para a App Store. O aplicativo não precisa ser baixado para testes.
1. Inicie o aplicativo pela primeira vez no mesmo dispositivo móvel que você usou na etapa 6.

   Você pode excluir e instalar o aplicativo novamente, se necessário.
1. (Opcional) Ative o registro de depuração do SDK para obter informações adicionais.

   Se tudo funcionar corretamente, você deverá ver os seguintes registros:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   Caso não veja esses logs, verifique se completou as etapas 4 e 5.

   Estas são algumas informações sobre possíveis erros:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`:

      Ocorreu um erro de rede.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      A resposta não está no formato correto.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      Não há um parâmetro `contextData` na resposta.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` não está `contextData`incluído.

   * `Analytics - Acquisition referrer timed out`

      Falha ao obter a resposta no tempo definido por `referrerTimeout`. Aumente o valor e tente novamente. Você também deve garantir que abriu o link de aquisição antes de instalar o aplicativo e que esteja usando a mesma rede quando clicar no URL e abrir o aplicativo.

Lembre-se das seguintes informações:

* O servidor de aquisição fornece uma correspondência de atribuição baseada no endereço IP e nas informações agente-usuário gravadas nos cliques em links (etapa 6) e quando o aplicativo é iniciado (etapa 7).

   Você deve estar na mesma rede quando clicar no URL e quando abrir o aplicativo.

* Ao usar ferramentas de monitoramento HTTP, as ocorrências enviadas pelo aplicativo podem ser monitoradas para fornecer a verificação da atribuição de aquisição.

   You should see one `/v3/<appid>/start` request and one `/v3/<appid>/end` request that are sent to the acquisition server.

* As variações no agente-usuário enviado podem causar falha na atribuição.

   Verifique `https://c00.adobe.com/v3/<appid>/start` e `https://c00.adobe.com/v3/<appid>/end` tenha os mesmos valores agente-usuário.

* O link de aquisição e a ocorrência do SDK devem usar o mesmo protocolo HTTP/HTTPS.

   Se o link e a ocorrência estiverem usando diferentes protocolos, onde o link usa HTTP e o SDK usa HTTPS, o endereço IP pode ser diferente em algumas operadoras para cada solicitação. Isso pode fazer com que a atribuição falhe.

* Os Links de marketing são armazenados em cache no lado do servidor com um tempo de expiração de dez minutos.

   Ao fazer alterações nos Links de publicidade, você deve aguardar cerca de 10 minutos antes de usar os links.