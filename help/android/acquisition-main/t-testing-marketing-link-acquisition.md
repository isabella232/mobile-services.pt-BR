---
description: As instruções a seguir ajudam a fazer uma viagem de ida e volta em uma campanha de aquisição com um link de marketing em um dispositivo Android.
keywords: android;biblioteca;móvel;sdk
solution: Experience Cloud Services,Analytics
title: Teste de aquisição de links de marketing
topic-fix: Developer and implementation
uuid: d0933dcc-8fc3-4f60-987f-7a54559aacf5
exl-id: 86fdaef7-5b6c-4e9d-a470-df66c96f2e9d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 100%

---

# Teste de aquisição de links de marketing {#testing-marketing-link-acquisition}

As instruções a seguir ajudam a fazer uma viagem de ida e volta em uma campanha de aquisição com um link de marketing em um dispositivo Android.

Se o aplicativo móvel ainda não estiver no Google Play, é possível selecionar qualquer aplicativo móvel como destino ao criar o link de marketing. Essa ação não afeta a capacidade de testar o link de aquisição, afeta somente o aplicativo para o qual você é redirecionado pelo servidor de aquisição após clicar no link. Os parâmetros da string de query são passados para a Google Play store, que são passados para o aplicativo na instalação como parte de uma transmissão de campanha. O teste de aquisição de aplicativo móvel de ida e volta requer a simulação desse tipo de transmissão.

O aplicativo deve estar recém-instalado ou ter os dados limpos em **[!UICONTROL Configurações]** sempre que um teste for executado. Isso garante que as medições de ciclo de vida inicial associadas aos parâmetros de cadeia de caracteres de consulta da campanha sejam enviadas quando o aplicativo é inicializado pela primeira vez.

1. Conclua as tarefas de pré-requisito na [Aquisição de aplicativos móveis](/help/android/acquisition-main/acquisition.md) e certifique-se de que você implementou corretamente o receptor de transmissão para `INSTALL_REFERRER`.
1. Na interface do Adobe Mobile Services, clique em **[!UICONTROL Aquisição]** > **[!UICONTROL Construtor de links de marketing]** e gere um URL de Aquisição de link de marketing que defina o Google Play como destino para dispositivos Android.

   Para obter mais informações, consulte [Criador de links de marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Por exemplo:

   `https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Abra o link gerado no dispositivo Android.

   Você deverá ser redirecionado a uma página com URL semelhante ao exemplo a seguir:

   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copie o identificador exclusivo depois de `utm_content%3D`.

   No exemplo anterior, a ID é `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

   Caso não consiga obter o identificador exclusivo no dispositivo, execute o comando `CURL` no desktop para obter o identificador exclusivo da cadeia de caracteres de resposta.

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" <Your Marketing Link>`

   Por exemplo:

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Construa o link final de aquisição usando o identificador exclusivo da etapa 3, no formato a seguir:

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`

   Por exemplo, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Abra o link no navegador.

   Você deverá ver o `contextData` na resposta do JSON:

   ```
   {"fingerprint":"44b2f88a062df7e727c047f006deb9971304617b","endCallbacks":["***"],"timestamp":1464301282,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData": 
   {"a.launch.campaign.trackingcode":"trymttvm","a.referrer.campaign.name":"Android Demo","a.referrer.campaign.trackingcode":"trymttvm"} 
   ,"adobeData":{"unique_id":"9a2be52764a8db125c29a8c10f3b1b3d5d8ed915","deeplinkid":"57476c26072932ec6d3a470b"}}.
   ```

1. Repita a etapa 3 para obter um novo identificador exclusivo.
1. Verifique se as seguintes configurações em seu arquivo de configuração estão corretas:

   | Configuração | Valor |
   |--- |--- |
   | aquisição | O servidor deve ser `c00.adobe.com`, e *`appid`* deve ser igual ao `appid` no link de aquisição. |
   | analytics | Para fins de teste, defina o tempo limite do referenciador para permitir o tempo adequado (60 segundos ou mais) para enviar manualmente a transmissão. É possível restaurar a configuração original de tempo limite após o teste. |

1. Conecte o dispositivo a um computador, desinstale e instale o aplicativo novamente.
1. Inicie o ADB Shell e execute o aplicativo no dispositivo.

   ```
   adb shell
   ```

1. Envie uma transmissão usando o comando `adb` a seguir:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"
   ```

1. Substitua o `com.adobe.android` pelo nome de pacote do aplicativo, atualize a referência do destinatário com a da localização do rastreamento de campanha no aplicativo e substitua os valores associados com `utm_content`.

   Se a transmissão for bem sucedida, você deve esperar uma resposta como o exemplo a seguir:

   ```
   Broadcasting: Intent 
   { act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
   Broadcast completed: result=0 
   ```

1. (Opcional) É possível ativar o registro de depuração do SDK para obter informações adicionais.

   Se tudo funcionar corretamente, você deverá ver os seguintes registros:

   ```
   "Analytics - Received referrer information(<referrer content>)" 
   "Analytics - Trying to fetch referrer data from (acquisition end url)"; 
   "Analytics - Received Referrer Data(<A JSON Response>)"
   ```

   Se não vir esses logs, verifique se você concluiu as etapas 6 a 10.

   A tabela a seguir contém informações adicionais sobre possíveis erros:

   | Erro | Descrição |
   |--- |--- |
   | Analytics - Unable to decode response(`<string>`). | A resposta está malformada. |
   | Analytics - Unable to parse response (`a JSON Response`). | A cadeia de caracteres JSON está malformada. |
   | Analytics - Unable to parse acquisition service response (no `contextData` parameter in response). | Não há um parâmetro `contextData` na resposta. |
   | Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` não está incluído em contextData. |
   | Analytics - Acquisition referrer timed out. | Falha ao obter a resposta no tempo definido pelo `referrerTimeout`. Aumente o valor e tente novamente.  Você também deve garantir que abriu o link de aquisição antes de instalar o aplicativo. |

Lembre-se das seguintes informações:

* As ocorrências enviadas pelo aplicativo podem ser monitoradas usando ferramentas de monitoramento HTTP para verificar a atribuição de aquisição.
* Para obter mais informações sobre como fazer a transmissão do `INSTALL_REFERRER`, consulte [Testar medição de campanha do Google Play](https://developers.google.com/analytics/solutions/testing-play-campaigns) no Guia de desenvolvedores do Google.
* É possível usar a ferramenta `acquisitionTest.jar` do Java fornecida para ajudá-lo a obter o identificador exclusivo e o referencial de instalação da transmissão que, por sua vez, o ajuda a obter as informações das etapas de 3 a 10.

**Instalação da ferramenta Java**

Para instalar a ferramenta Java:

1. Baixe o arquivo [`acquistionTester.zip`](../assets/acquisitionTester.zip).
1. Extraia o arquivo .jar.

   Você pode executar o arquivo .jar na linha de comando.

Por exemplo:

```
java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
```

Os Links de marketing são armazenados em cache no lado do servidor com um tempo de expiração de dez minutos. Ao fazer alterações nos links de marcação, espere cerca de 10 minutos para que as alterações façam efeito antes de usar os links novamente.
