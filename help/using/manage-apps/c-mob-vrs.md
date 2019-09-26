---
description: Um conjunto de relatórios virtual (VRS) é um conjunto de relatórios que é criado ao aplicar uma ou mais definições de segmento a um conjunto de relatórios. Isso permite aos usuários manter seus dados em um conjunto de relatórios, mas gerenciar os dados como se estivessem em conjuntos de relatórios separados.
seo-description: Um conjunto de relatórios virtual (VRS) é um conjunto de relatórios que é criado ao aplicar uma ou mais definições de segmento a um conjunto de relatórios. Isso permite aos usuários manter seus dados em um conjunto de relatórios, mas gerenciar os dados como se estivessem em conjuntos de relatórios separados.
seo-title: Conjuntos de relatórios virtuais
title: Conjuntos de relatórios virtuais
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febd
translation-type: tm+mt
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# Virtual report suites {#virtual-report-suites}

Um conjunto de relatórios virtual (VRS) é um conjunto de relatórios que é criado ao aplicar uma ou mais definições de segmento a um conjunto de relatórios. Isso permite que os usuários mantenham seus dados em um conjunto de relatórios, mas gerenciem os dados como se estivessem em conjuntos de relatórios separados.

Os aplicativos que usam VRSs fazem o mesmo que os aplicativos que usam um conjunto de relatórios regular, exceto para gerenciar os seguintes recursos:

* Regras de processamento
* evars/props/listvars/eventos
* Opção ativada por carimbo de data e hora
* Sinalizadores de dimensão (ciclo de vida, localização e assim por diante)
* Classificações

Esses valores são gerenciados no conjunto de relatórios principal e são compartilhados com os VRSs que pertencem ao mesmo conjunto principal.

As seguintes áreas podem ser acessadas na interface do usuário do Adobe Mobile Services, independentemente do conjunto de relatórios principal:

* O arquivo de configuração
* Gerenciar pontos de interesse
* Gerenciar destinos de links
* Gerenciar postbacks
* Links de mensagem
* Aquisição

Um VRS pode ajudá-lo a concluir as seguintes tarefas:

* Restringir o acesso aos dados

   Uma empresa multinacional possui um aplicativo que envia dados para um conjunto de relatórios de todas as localizações geográficas. Entretanto, a empresa quer proibir que o usuário corporativo de uma região visualize os dados de outra região. The company’s admin can create a VRS to segment users by region and give permission to the VRS only to the business user who manages the region.

   Essa restrição impede que os usuários corporativos vejam dados que não estão relacionados à sua região. Por exemplo, um usuário corporativo na EMEA não precisa ver os dados da região APAC.

* Permita o controle de mensagens no aplicativo/push, POIs de localização, aquisição e postbacks, com todos os dados sendo enviados para um conjunto de relatórios.

   Uma empresa multinacional deseja que todos os dados sejam enviados para o mesmo conjunto de relatórios de todas as localizações geográficas. Entretanto, a empresa quer que a equipe de marketing de cada região controle suas próprias mensagens de push/no aplicativo. O administrador da empresa pode criar VRSs regionais e cada equipe pode gerenciar seu próprio aplicativo com base nesse VRS.

   A equipe regional cria o aplicativo usando o arquivo de configuração do VRS. Os dados são enviados para o conjunto de relatórios principal, mas as mensagens no aplicativo/push, os POIs de localização, a aquisição e os postbacks são controlados no aplicativo criado a partir do VRS.

## Create a virtual report suite in Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Somente os administradores do Adobe Analytics podem criar e modificar conjuntos de relatórios virtuais no Adobe Analytics. To create a virtual report suite, see [Create virtual report suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html).

Cada VRS possui uma ID exclusiva. Para exibir a ID do conjunto de relatórios principal na interface do usuário do Adobe Mobile Services, na página Gerenciar configurações do aplicativo, na seção Informações **[!UICONTROL do]** aplicativo, clique em **[!UICONTROL Mais detalhes]**.

Na interface do usuário do Adobe Mobile Services, você pode usar um VRS para criar um aplicativo e segmentar os dados para um grupo específico na organização. Desta forma, por exemplo, um usuário corporativo na Espanha não poderá ver os dados relevantes para um usuário corporativo no Japão.

>[!TIP]
>
>You cannot modify the values that are inherited from the parent report suite.

Um VRS é uma definição de segmento do lado do servidor que está anexada a um conjunto de relatórios principal. Como resultado, você não pode executar a coleta de dados para um VRS, já que o SDK envia ocorrências apenas ao conjunto de relatórios principal, o que, por sua vez, registra as ocorrências.

## Virtual report suite in Adobe Mobile Services and data collection {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

No Adobe Mobile Services, você pode criar um aplicativo com base em um conjunto de relatórios principal ou virtual. Ao criar um aplicativo com base em um conjunto de relatórios virtual, recomendamos que você alinhe o segmento do VRS com a definição do aplicativo.

>[!TIP]
>
>As certificações de push são anexadas no nível do aplicativo na interface do usuário do Mobile Services.

Para garantir que suas mensagens de push sejam enviadas corretamente, o segmento de público-alvo deve estar corretamente definido. Para obter mais informações, consulte [Público-alvo: Defina e configure os segmentos de público-alvo para mensagens](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md)de push.

## Understanding time zones {#section_498E1EED22D741C3BDED44F01FACA72A}

A propriedade de fuso horário na página Gerenciar configurações do aplicativo é diferente da propriedade de fuso horário usada para criar o VRS no Adobe Analytics. A propriedade na página Gerenciar configurações do aplicativo é herdada do conjunto de relatórios principal, que é usado para enviar dados para o Adobe Analytics. A propriedade especificada ao criar o VRS no Adobe Analytics é usada para exibir os relatórios na interface do usuário do Mobile Services e pode ser diferente do conjunto de relatórios principal.

## Select a virtual report suite in the Mobile Services UI {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

Para usar um VRS ao criar um aplicativo, selecione o VRS na lista suspensa **[!UICONTROL Conjunto de relatórios]** na página Informações do aplicativo. Esta lista contém conjuntos de relatórios principais e virtuais.

>[!IMPORTANT]
>
>To select a VRS from the list, locate an option with the blue dot and the `vrs_` *`<company_name>`* `_` *`<unique name>`* naming convention.

## Virtual Report Suite properties {#section_20ECE6243F664C4FB4347ADB4FF0458A}

Estas são as propriedades de VRSs:

>[!TIP]
>
>As propriedades somente leitura são herdadas do conjunto de relatórios pai.

| Propriedade | Herdado do conjunto de relatórios principal | Editável? | Notas |
|--- |--- |--- |--- |
| `target.clientCode` | Não | Sim |  |
| `target.timeout` | Não | Sim |  |
| `audienceManager.server` | Não | Sim |  |
| `audienceManager.analyticsForwardingEnabled` | Sim | Sim |  |
| `audienceManager.timeout` | Não | Sim |  |
| `acquisition.server` | Não | Não |  |
| `acquisition.appid` | Não | Não |  |
| `analytics.rsids` | Sim | Não |  |
| `analytics.server` | Não | Não |  |
| `analytics.ssl` | Não | Sim |  |
| `analytics.offlineEnabled` | Sim |  |  |
| `analytics.charset` | Sim | Não |  |
| `analytics.lifecycleTimeout` | Não | Sim | Deve ser o conjunto de relatórios principal, se os usuários não quiserem que seus dados sejam inconsistentes. |
| `analytics.privacyDefault` | Não | Sim |  |
| `analytics.batchLimit` | Não | Sim |  |
| `analytics.timezone` | Sim | Sim, quando você cria o aplicativo pela primeira vez. | Esta propriedade de fuso horário é usada para enviar dados ao Adobe Analytics e é diferente da propriedade de fuso horário que é definida quando um VRS é criado. |
| `analytics.timezoneOffset` | Sim | Não |  |
| `analytics.referrerTimeout` | Não | Sim |  |
| `analytics.backdateSessionInfo` | Sim | Sim |  |

## Informações adicionais {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

Estas são algumas informações adicionais sobre conjuntos de relatórios virtuais:

* Para obter mais informações sobre VRSs, consulte [Conjuntos de relatórios virtuais](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-about.html).
* For more information about planning a VRS implementation, see [Virtual report suite workflow](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).