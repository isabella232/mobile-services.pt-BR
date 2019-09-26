---
description: Esta informação ajuda a redirecionar um link de campanha de aquisição V3 com base em uma impressão digital do dispositivo.
seo-description: Esta informação ajuda a redirecionar um link de campanha de aquisição V3 com base em uma impressão digital do dispositivo.
seo-title: Testar aquisição da V3
solution: Marketing Cloud,Analytics
title: Testar aquisição da V3
uuid: 89137ccf-4839-4b37-926e-303cf8e511a5
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Testing V3 acquisition{#testing-v-acquisition}

Esta informação ajuda a redirecionar um link de campanha de aquisição V3 com base em uma impressão digital do dispositivo.

>[!IMPORTANT]
>
>V3 Acquisition refers to the acquisition links that you create with the Acquisition Builder in the Adobe Mobile Services UI. Para usar esse recurso, você deve atualizar para o SDK do iOS versão 4.6.0 ou posterior.

Se o aplicativo móvel ainda não estiver na App Store, ao criar o link da campanha, selecione qualquer aplicativo móvel como destino. Isso afeta somente o aplicativo ao qual o servidor de aquisição redireciona você depois de clicar no link de aquisição, mas não afeta a capacidade de testar o link.

1. Conclua as tarefas de pré-requisito na Aquisição [](/help/ios/acquisition-main/acquisition.md)de aplicativos para dispositivos móveis.
1. Navigate to the **[!UICONTROL Acquisition Builder]** in the Adobe Mobile Services UI and generate an acquisition campaign URL.

   Por exemplo:

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   Se você se referir aos aplicativos iOS e Android no link de aquisição, use a Apple Store como a loja padrão.
1. Open the generated link in a desktop browser and go to `https://c00.adobe.com/v3/<appid>/end`.

   Você deve ver o `contextData` na resposta JSON:

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   If you do not see `contextData`, or some of it is missing, ensure that the acquisition URL follows the format that is specified in [Create Acquisition Link Manually](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Verifique se as seguintes configurações em seu arquivo de configuração estão corretas:

   | Configuração | Valor |
   |--- |--- |
   | aquisição | The server should be  `c00.adobe.com`. *`appid`* deve ser igual ao *`appid`* no link de aquisição. |
   | analytics | `referrerTimeout` deve ter um valor maior que 0. |


1. (Condicional) Se a configuração `ssl` no arquivo de configuração do seu aplicativo for verdadeira, atualize seu link de aquisição para usar o protocolo HTTPS.
1. Clique no link gerado no dispositivo móvel no qual você planeja instalar o aplicativo.

   Os servidores da Adobe ( `c00.adobe.com` ) armazenam a impressão digital e redirecionam para a App Store. O aplicativo não precisa ser baixado para testes.
1. Inicie o aplicativo pela primeira vez no mesmo dispositivo móvel que você usou na etapa 6.

   Você pode excluir e instalar o aplicativo novamente, se necessário.
1. (Opcional) É possível ativar o registro de depuração do SDK para obter informações adicionais.

   Se tudo funcionar corretamente, você deverá ver os seguintes registros:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   Se você não vir os registros acima, verifique se concluiu as etapas 4 e 5.

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

      Falha ao obter a resposta no tempo definido por `referrerTimeout`. Aumente o valor e tente novamente. Você também deve garantir que abriu o link de aquisição antes de instalar o aplicativo e que esteja usando a mesma rede quando clicar no URL e abrir o aplicativo.

      Lembre-se das seguintes informações:

      * O servidor de aquisição fornece uma correspondência de atribuição baseada no endereço IP e nas informações agente-usuário gravadas aos cliques em links (etapa 6) e quando o aplicativo é iniciado (etapa 7).

         Você deve estar na mesma rede quando clicar no URL e quando abrir o aplicativo.

      * Ao usar ferramentas de monitoramento HTTP, as ocorrências enviadas pelo aplicativo podem ser monitoradas para fornecer a verificação da atribuição de aquisição.

         You should see one `/v3/<appid>/start` request and one `/v3/<appid>/end` request sent to the acquisition server. As variações no agente-usuário enviado podem causar falha na atribuição.

         >[!TIP]
         >
         >Certifique-se de que `https://c00.adobe.com/v3/<appid>/start` e que `https://c00.adobe.com/v3/<appid>/end` tenham os mesmos valores agente-usuário.

      * O link de aquisição e a ocorrência do SDK devem usar o mesmo protocolo HTTP/HTTPS.

         Se estiverem usando diferentes protocolos (por exemplo, o link usa HTTP e o SDK, HTTPS), o endereço IP poderá ser diferente para cada solicitação (em algumas operadoras) e a atribuição poderá falhar.
