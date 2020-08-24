---
description: As instruções a seguir ajudam a redirecionar uma campanha de aquisição com um link de marketing baseado em uma impressão digital do dispositivo.
keywords: android;library;mobile;sdk
seo-description: As instruções a seguir ajudam a redirecionar uma campanha de aquisição com um link de marketing baseado em uma impressão digital do dispositivo.
seo-title: Teste de aquisição de links de marketing
solution: Marketing Cloud,Analytics
title: Teste de aquisição de links de marketing
topic: Developer and implementation
uuid: 69503e01-182d-44c6-b0fb-e1c012ffa3bd
translation-type: ht
source-git-commit: c64e2fa7cee3cd35c4574e5007406b7604c99499
workflow-type: ht
source-wordcount: '562'
ht-degree: 100%

---


# Teste de aquisição de links de marketing {#testing-marketing-link-acquisition}

As instruções a seguir ajudam a redirecionar uma campanha de aquisição com um link de marketing baseado em uma impressão digital do dispositivo.

1. Conclua as tarefas de pré-requisito na [Aquisição de aplicativos para dispositivos móveis](/help/ios/acquisition-main/acquisition.md).
1. Na interface do usuário dos Adobe Mobile Services, clique em **[!UICONTROL Criador de links de marketing]** e gere um URL de link de marketing de aquisição que estabeleça a App Store como destino para dispositivos iOS.

   Por exemplo:

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   Para obter mais informações, consulte [Criador de links de marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).


1. Abra o link gerado no dispositivo iOS e abra `https://c00.adobe.com/v3/<appid>/end`.

   Você deve ver o contextData na resposta JSON:

   ```js
   {"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. Verifique se as seguintes configurações em seu arquivo de configuração estão corretas:

   | Configuração | Valor |
   |--- |--- |
   | aquisição | O servidor deve ser `c00.adobe.com`. `appid` deve ser igual ao *`appid`* no link de aquisição. |
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

   Se você não vir os registros acima, verifique se completou as etapas 4 e 5.

   Estas são algumas informações sobre possíveis erros:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`

      Ocorreu um erro de rede.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      A resposta não está no formato correto.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      Não há um parâmetro `contextData` na resposta.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` não está incluído em `contextData`.

   * `Analytics - Acquisition referrer timed out`

      Falha ao obter a resposta no tempo definido por `referrerTimeout`. Aumente o valor e tente novamente. Você também deve garantir que abriu o link de aquisição antes de instalar o aplicativo e que está usando a mesma rede ao clicar no URL e abrir o aplicativo.

Lembre-se das seguintes informações:

* O servidor de aquisição fornece uma correspondência de atribuição baseada no endereço IP e nas informações agente-usuário gravadas nos cliques em links (etapa 6) e quando o aplicativo é iniciado (etapa 7).

   Você deve estar na mesma rede quando clicar no URL e quando abrir o aplicativo.

* Ao usar ferramentas de monitoramento HTTP, as ocorrências enviadas pelo aplicativo podem ser monitoradas para fornecer a verificação da atribuição de aquisição.

   Você deve ver uma solicitação `/v3/<appid>/start` e uma solicitação `/v3/<appid>/end` enviadas ao servidor de aquisição.

* As variações no agente-usuário enviado podem causar falha na atribuição.

   Certifique-se de que `https://c00.adobe.com/v3/<appid>/start` e `https://c00.adobe.com/v3/<appid>/end` tenham os mesmos valores de agente-usuário.

* O link de aquisição e a ocorrência do SDK devem usar o mesmo protocolo HTTP/HTTPS.

   Se o link e a ocorrência estiverem usando diferentes protocolos, em que, por exemplo, o link usa HTTP e o SDK usa HTTPS, o endereço IP poderá ser diferente para cada solicitação em algumas operadoras. Isso pode fazer com que a atribuição falhe.

* Os Links de marketing são armazenados em cache no lado do servidor com um tempo de expiração de dez minutos.

   Quando você faz alterações em links de marketing, deve aguardar cerca de 10 minutos antes de usar os links.