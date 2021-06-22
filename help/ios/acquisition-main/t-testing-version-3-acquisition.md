---
description: Esta informação ajuda a redirecionar um link de campanha de aquisição V3 com base em uma impressão digital do dispositivo.
seo-description: Esta informação ajuda a redirecionar um link de campanha de aquisição V3 com base em uma impressão digital do dispositivo.
seo-title: Teste da aquisição V3
solution: Experience Cloud,Analytics
title: Teste da aquisição V3
uuid: 89137ccf-4839-4b37-926e-303cf8e511a5
exl-id: 3cf66802-1f2c-428f-86ef-a9afc57e3470
source-git-commit: 8db8f51a42acbbc0bbc4545b7d97cb214b490ab3
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 100%

---

# Teste da aquisição V3 {#testing-v-acquisition}

Esta informação ajuda a redirecionar um link de campanha de aquisição V3 com base em uma impressão digital do dispositivo.

>[!IMPORTANT]
>
>A aquisição V3 se refere aos links de aquisição criados com o Criador de aquisição na interface do Adobe Mobile Services. Para usar esse recurso, é necessário atualizar para o iOS SDK versão 4.6.0 ou posterior.

Se o aplicativo móvel ainda não estiver na App Store, ao criar o link de campanha, selecione qualquer aplicativo móvel como destino. Essa ação só afeta o aplicativo para o qual o servidor de aquisição o redireciona após clicar no link de aquisição, mas não afeta a capacidade de testar o link.

1. Conclua as tarefas de pré-requisito na [Aplicativo móvel do Acquisition](/help/ios/acquisition-main/acquisition.md).
1. Navegue até o **[!UICONTROL Criador de aquisição]** na interface do usuário dos Adobe Mobile Services e gere um URL de campanha de aquisição.

   Por exemplo:

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   Se você fizer referência aos aplicativos iOS e Android no link de aquisição, use a Apple Store como a loja padrão.
1. Abra o link gerado em um navegador de desktop e vá para `https://c00.adobe.com/v3/<appid>/end`.

   Você deve ver o `contextData` na resposta JSON:

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   Se você não vir `contextData`, ou parte dos dados estiver ausente, verifique se o URL de aquisição segue o formato especificado em [Criar link de aquisição manualmente](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Verifique se as seguintes configurações em seu arquivo de configuração estão corretas:

   | Configuração | Valor |
   |--- |--- |
   | aquisição | O servidor deve ser `c00.adobe.com`. *`appid`* deve ser igual ao *`appid`* no link de aquisição. |
   | analytics | `referrerTimeout` deve ter um valor maior que 0. |


1. (Condicional) Se a configuração `ssl` no arquivo de configuração do seu aplicativo for verdadeira, atualize seu link de aquisição para usar o protocolo HTTPS.
1. Clique no link gerado pelo dispositivo móvel no qual você planeja instalar o aplicativo.

   Os servidores da Adobe ( `c00.adobe.com` ) armazenam a impressão digital e redirecionam para a App Store. O aplicativo não precisa ser baixado para testes.
1. Inicie o aplicativo pela primeira vez no mesmo dispositivo móvel que você usou na etapa 6.

   Você pode excluir e instalar o aplicativo novamente, se necessário.
1. (Opcional) É possível ativar o registro de depuração do SDK para obter informações adicionais.

   Se tudo funcionar corretamente, você deverá ver os seguintes registros:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   Se você não vir os registros acima, verifique se as etapas 4 e 5 foram concluídas.

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

      * O servidor de aquisição fornece uma correspondência de atribuição baseada no endereço IP e nas informações agente-usuário gravadas aos cliques em links (etapa 6) e quando o aplicativo é iniciado (etapa 7).

         Você deve estar na mesma rede quando clicar no URL e quando abrir o aplicativo.

      * Ao usar ferramentas de monitoramento HTTP, as ocorrências enviadas pelo aplicativo podem ser monitoradas para fornecer a verificação da atribuição de aquisição.

         Você deve ver uma solicitação `/v3/<appid>/start` e uma solicitação `/v3/<appid>/end` enviadas ao servidor de aquisição. As variações no agente-usuário enviado podem causar falha na atribuição.

         >[!TIP]
         >
         >Certifique-se de que `https://c00.adobe.com/v3/<appid>/start` e `https://c00.adobe.com/v3/<appid>/end` tenham os mesmos valores de agente-usuário.

      * O link de aquisição e a ocorrência do SDK devem usar o mesmo protocolo HTTP/HTTPS.

         Se estiverem usando diferentes protocolos (por exemplo, o link usa HTTP e o SDK, HTTPS), o endereço IP poderá ser diferente para cada solicitação (em algumas operadoras) e a atribuição poderá falhar.
