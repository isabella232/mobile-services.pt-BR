---
description: Estas informações ajudam a fazer uma viagem de ida e volta no link da campanha de aquisição da versão 3 em um dispositivo Android.
keywords: android;biblioteca;móvel;sdk
seo-description: Estas informações ajudam a fazer uma viagem de ida e volta no link da campanha de aquisição da versão 3 em um dispositivo Android.
seo-title: Testar a Aquisição versão 3
solution: Experience Cloud,Analytics
title: Testar a Aquisição versão 3
topic-fix: Developer and implementation
uuid: 5e38b43d-389e-4412-99e5-3e6223b6ad28
exl-id: 2ce78e2e-da51-4af8-a461-ec6c642a7854
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 100%

---

# Teste da aquisição V3 {#testing-version-acquisition}

Estas informações ajudam a fazer uma viagem de ida e volta no link da campanha de aquisição da versão 3 em um dispositivo Android.

>[!IMPORTANT]
>
>A aquisição V3 se refere aos links de aquisição criados com o Criador de aquisição na interface do Adobe Mobile Services. Para usar esse recurso, você deve atualizar para o Android SDK 4.x para as soluções da Experience Cloud 4.6.0 ou posterior.

Se o aplicativo móvel ainda não estiver no Google Play, ao criar o link de campanha, você pode selecionar qualquer aplicativo móvel como destino. Essa ação só afeta o aplicativo para o qual o servidor de aquisição o redireciona após clicar no link de aquisição, mas não afeta a capacidade de testar o link. Os parâmetros da string de query são passados para a Google Play store, que são passados para o aplicativo na instalação como parte de uma transmissão de campanha. O teste de aquisição de aplicativo móvel de ida e volta requer a simulação desse tipo de transmissão.

>[!IMPORTANT]
>
>Se você estiver fazendo uma implementação usando as APIs do Referenciador de instalação do Google Play, não será possível testar a aquisição antes que seu aplicativo esteja na Google Play Store.

O aplicativo deve estar recém-instalado ou ter os dados limpos em **[!UICONTROL Configurações]** sempre que um teste for executado. Isso garante que as medições de ciclo de vida inicial associadas aos parâmetros de cadeia de caracteres de consulta da campanha sejam enviadas quando o aplicativo é inicializado pela primeira vez.

1. Conclua as tarefas de pré-requisito na [Aquisição de aplicativos móveis](/help/android/acquisition-main/acquisition.md) e certifique-se de que você implementou corretamente o receptor de transmissão para `INSTALL_REFERRER`.

1. Na interface do Adobe Mobile Services, clique em **[!UICONTROL Aquisição]** > **[!UICONTROL Construtor de links de marketing]** e gere um URL de Aquisição de link de marketing que defina o Google Play como destino para dispositivos Android.

   Para obter mais informações, consulte [Criador de links de marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Por exemplo, `https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=g&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode`.

   >[!TIP]
   >
   >Se fizer referência aos aplicativos do Android ou iOS no link de aquisição, use o Google Play como loja padrão.

1. Abra o link em um navegador do desktop.

   Você deverá ser redirecionado a uma página com URL semelhante ao exemplo a seguir:
   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copie o identificador exclusivo depois de `utm_content%3D`.

   No exemplo anterior, a ID é `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Construa o link final de aquisição usando o identificador exclusivo da etapa 3, usando o formato a seguir:

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`.

   Por exemplo, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Abra o link em um navegador do desktop.

   Você deverá ver o `contextData` na resposta do JSON:

   `{"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.`

   Se você não visualizar `contextData` ou se estiver faltando uma cadeia de caracteres, certifique-se de que o URL de aquisição siga o formato em [Criar link de aquisição manualmente](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Repita a etapa 3 para obter um novo identificador exclusivo.
1. Verifique se as seguintes configurações em seu arquivo de configuração estão corretas:

   | Configuração | Valor |
   |--- |--- |
   | aquisição | O servidor deve ser `c00.adobe.com`. *`appid`* deve ser igual ao `appid` no link de aquisição. |
   | analytics | Para fins de teste, defina o tempo limite do referenciador para permitir o tempo adequado (60 segundos ou mais) para enviar manualmente a transmissão. É possível restaurar a configuração original de tempo limite após o teste. |

1. Conecte o dispositivo a um computador, desinstale e instale o aplicativo novamente.
1. Inicie o ADB Shell e execute o aplicativo no dispositivo.
1. Envie uma transmissão usando o comando `adb` a seguir:

   `am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"`

1. Complete as etapas a seguir:
   1. Substitua `com.adobe.android` pelo nome de pacote do aplicativo.
   1. Atualize a referência do receptor com a da localização do receptor de rastreamento de campanha no aplicativo
   1. Substitua os valores associados ao `utm_content`.

   Se a transmissão for bem sucedida, você pode esperar uma resposta como o exemplo a seguir:

   `Broadcasting: Intent
{ act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) }
Broadcast completed: result=0`

1. (Opcional) É possível ativar o registro de depuração do SDK para obter informações adicionais.

   Se tudo funcionar corretamente, você deverá ver os seguintes registros:

`"Analytics - Received referrer information(<referrer content>)"   "Analytics - Trying to fetch referrer data from (acquisition end url)"; "Analytics - Received Referrer Data(<A JSON Response>)"`

Se você não vir os registros acima, verifique se completou as etapas 6 a 12.

A tabela a seguir contém informações adicionais sobre possíveis erros:

| Erro | Descrição |
|--- |--- |
| Analytics - Unable to decode response(*String*). | A resposta está malformada. |
| Analytics - Unable to parse response (*a JSON Response*). | A cadeia de caracteres JSON está malformada. |
| Analytics - Unable to parse acquisition service response (no contextData parameter in response). | Não há um parâmetro contextData na resposta. |
| Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` não está incluído em  contextData. |
| Analytics - Acquisition referrer timed out. | Falha ao obter a resposta no tempo definido pelo `referrerTimeout`. Aumente o valor e tente novamente.  Você também deve garantir que abriu o link de aquisição antes de instalar o aplicativo. |

Lembre-se das seguintes informações:

* As ocorrências enviadas pelo aplicativo podem ser monitoradas usando ferramentas de monitoramento HTTP para verificar a atribuição de aquisição.
* Para obter mais informações sobre como fazer a transmissão do `INSTALL_REFERRER`, consulte [Testar medição de campanha do Google Play](https://developers.google.com/analytics/solutions/testing-play-campaigns) no Guia de desenvolvedores do Google.

* Uma correção de erro foi lançada para aquisição no Android 4.8.2.

   Antes de testar, atualize o SDK para a versão mais recente.

* É possível usar a ferramenta `acquisitionTest.jar` do Java fornecida para ajudá-lo a obter o identificador exclusivo e o referencial de instalação da transmissão que, por sua vez, o ajuda a obter as informações das etapas de 3 a 12.

   **Instalação da ferramenta Java**

Para instalar a ferramenta Java:

1. Baixe o arquivo [`acquisitionTester.zip`](/help/android/assets/acquisitionTester.zip).

1. Extraia o arquivo .jar.

   Você pode executar o arquivo na linha de comando.

   Por exemplo:

   ```java
   java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
   ```
