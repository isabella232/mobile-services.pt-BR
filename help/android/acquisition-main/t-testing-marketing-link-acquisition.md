---
description: As instruções a seguir ajudam a redirecionar uma campanha de aquisição com um Marketing Link em um dispositivo Android.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: As instruções a seguir ajudam a redirecionar uma campanha de aquisição com um Marketing Link em um dispositivo Android.
seo-title: Testar a aquisição de links de marketing
solution: Marketing Cloud, Analytics
title: Testar a aquisição de links de marketing
topic: Desenvolvedor e implementação
uuid: d 0933 dcc -8 fc 3-4 f 60-987 f -7 a 54559 aacf 5
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

As instruções a seguir ajudam a redirecionar uma campanha de aquisição com um Marketing Link em um dispositivo Android.

Se o aplicativo móvel ainda não estiver no Google Play, você pode selecionar qualquer aplicativo móvel como destino ao criar o Marketing Link. Isso não afeta a capacidade de testar o link de aquisição, somente o aplicativo para o qual você é redirecionado pelo servidor de aquisição após clicar no link. Os parâmetros da cadeia de caracteres de consulta são passados para a Google Play store, que é passada para o aplicativo na instalação como parte de uma difusão de campanha. A viagem de ida e volta do teste de aquisição do aplicativo móvel requer uma simulação desse tipo de difusão.

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. Isso garante que as medições de ciclo de vida inicial associadas aos parâmetros de cadeia de caracteres de consulta da campanha sejam enviadas quando o aplicativo é inicializado pela primeira vez.

1. Conclua as tarefas de pré-requisito na [aquisição](/help/android/acquisition-main/acquisition.md) do aplicativo móvel e certifique-se `INSTALL_REFERRER`de implementá-lo corretamente.
1. In the Adobe Mobile Services] UI, click  **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Links Builder]** and generate an Acquisition Marketing Link URL that sets Google Play as the destination for Android devices.

   Para obter mais informações, consulte [Criador de links de marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Por exemplo:

   `https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Abra o link gerado no dispositivo Android.

   Você deverá ser redirecionado a uma página com URL semelhante ao exemplo a seguir:

   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copy the unique ID after `utm_content%3D`.

   No exemplo anterior, a ID é `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

   Caso não consiga obter a ID única no dispositivo, execute o comando `CURL` no desktop para obter a ID única da cadeia de caracteres de resposta.

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" <Your Marketing Link>`

   Por exemplo:

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Construa o link final de aquisição usando a ID única da etapa 3, no formato a seguir:

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`

   Por exemplo, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Abra o link no navegador.

   Você deverá ver o `contextData` na resposta do JSON:

   ```
   {"fingerprint":"44b2f88a062df7e727c047f006deb9971304617b","endCallbacks":["***"],"timestamp":1464301282,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData": 
   {"a.launch.campaign.trackingcode":"trymttvm","a.referrer.campaign.name":"Android Demo","a.referrer.campaign.trackingcode":"trymttvm"} 
   ,"adobeData":{"unique_id":"9a2be52764a8db125c29a8c10f3b1b3d5d8ed915","deeplinkid":"57476c26072932ec6d3a470b"}}.
   ```

1. Repita a etapa 3 para obter ima ID única.
1. Verifique se as seguintes configurações em seu arquivo de configuração estão corretas:

   | Configuração | Valor |
   |--- |--- |
   | aquisição | O servidor deve ser `c00.adobe.com`e *`appid`* deve ser igual ao `appid` do link de aquisição. |
   | analytics | Para fins de teste, defina o limite de tempo do referencial para permitir que o tempo adequado (60 segundos ou mais) envie a difusão automaticamente. É possível restaurar a configuração original de limite de tempo após testar. |

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

   Caso não veja esses logs, certifique-se de que tenha executado as etapas de 6 a 10.

   A tabela a seguir contém informações adicionais sobre os erros possíveis:

   | Erro | Descrição |
   |--- |--- |
   | Analytics - Unable to decode response(`<string>`). | A resposta está malformada. |
   | Analytics - Unable to parse response (`a JSON Response`). | A cadeia de caracteres JSON está malformada. |
   | Analytics - Unable to parse acquisition service response (no `contextData` parameter in response). | Não há um parâmetro `contextData` na resposta. |
   | Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` não está incluída em contextdata. |
   | Analytics - tempo limite do referenciador de aquisição. | Falha ao obter a resposta no tempo definido pelo `referrerTimeout`. Aumente o valor e tente novamente.  Também é necessário ter certeza de que você abriu o link de aquisição antes de instalar o aplicativo. |

Lembre-se das seguintes informações:

* As ocorrências enviadas pelo aplicativo podem ser monitoradas usando as ferramentas de monitoramento HTTP para verificar a atribuição da aquisição.
* Para obter mais informações sobre como fazer a transmissão do `INSTALL_REFERRER`, consulte [Testar medida de campanha do Google Play](https://developers.google.com/analytics/solutions/testing-play-campaigns) no Guia de desenvolvedores do Google.
* É possível usar a ferramenta `acquisitionTest.jar` do Java fornecida para ajudá-lo a obter a ID única e o referencial de instalação da transmissão que, por sua vez, o ajuda a obter as informações das etapas de 3 a 10.

**Instalar a ferramenta Java**

Para instalar a ferramenta Java:

1. Download the [`acquistionTester.zip`](../assets/acquisitionTester.zip) file.
1. Extraia o arquivo .jar.

   É possível executar o arquivo .jar na linha de comando.

Por exemplo:

```
java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
```

Os Links de marketing são armazenados em cache no lado do servidor com um tempo de expiração de dez minutos. Ao fazer alterações nos links de marcação, espere cerca de 10 minutos para que as alterações façam efeito antes de usar os links novamente.
