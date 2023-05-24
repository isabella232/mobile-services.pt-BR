---
description: Um conjunto de relatórios virtual (VRS) é um conjunto de relatórios que é criado ao aplicar uma ou mais definições de segmento a um conjunto de relatórios. Isso permite aos usuários manter seus dados em um conjunto de relatórios, mas gerenciar os dados como se estivessem em conjuntos de relatórios separados.
title: Conjuntos de relatórios virtuais
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
exl-id: c9ce7f7c-2023-4a9d-9e4d-bacc21f9ad40
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 76%

---

# Conjuntos de relatórios virtuais {#virtual-report-suites}

{#eol}

Um conjunto de relatórios virtual (VRS) é um conjunto de relatórios que é criado ao aplicar uma ou mais definições de segmento a um conjunto de relatórios. Isso permite que os usuários mantenham seus dados em um conjunto de relatórios, mas gerenciem os dados como se estivessem em conjuntos de relatórios separados.

O procedimento dos aplicativos que usam VRSs é igual ao dos aplicativos que usam conjunto de relatórios, exceto para o gerenciamento dos seguintes recursos:

* Regras de processamento
* eVars/props/listvars/events
* Opção ativada por carimbo de data e hora
* Sinalizadores de Dimension (ciclo de vida, local e assim por diante)
* Classificações

Esses valores são gerenciados no conjunto de relatórios principal e compartilhados com os VRSs que pertencem ao mesmo conjunto de relatórios principal.

As seguintes áreas podem ser acessadas na interface do usuário do Adobe Mobile Services, independentemente do conjunto de relatórios principal:

* O arquivo de configuração
* Gerenciar pontos de interesse
* Gerenciar destinos de links
* Gerenciar postbacks
* Links de mensagem
* Aquisição

Um VRS pode ajudar a concluir as seguintes tarefas:

* Restringir o acesso aos dados

   Uma empresa multinacional tem um aplicativo que envia dados a um conjunto de relatórios para todas as localizações geográficas. Entretanto, a empresa quer proibir que o usuário corporativo de uma região visualize os dados de outra região. O administrador da empresa pode criar um VRS para segmentar os usuários por região e conceder permissão ao VRS somente para o usuário empresarial que gerencia a região.

   Essa restrição impede que os usuários corporativos vejam dados que não estão relacionados à sua região. Por exemplo, um usuário corporativo na EMEA não precisa ver os dados da região APAC.

* Permitir o controle de mensagens no aplicativo/por push, POIs de localização, aquisição e postbacks com todos os dados que estejam sendo enviados para um conjunto de relatórios.

   Uma empresa multinacional deseja que todos os dados sejam enviados para o mesmo conjunto de relatórios de todas as localizações geográficas. Entretanto, a empresa quer que a equipe de marketing de cada região controle suas próprias mensagens de push/no aplicativo. O administrador da empresa pode criar VRSs regionais e cada equipe pode gerenciar seu próprio aplicativo com base nesse VRS.

   A equipe regional cria o aplicativo usando o arquivo de configuração do VRS. Os dados são enviados para o conjunto de relatórios principal, mas as mensagens por push/no aplicativo, os POIs de localização, as aquisições e os postbacks são controlados no aplicativo criado a partir do VRS.

## Criar um conjunto de relatórios virtual no Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Somente os administradores do Adobe Analytics podem criar e alterar conjuntos de relatórios virtuais no Adobe Analytics. Para criar um conjunto de relatórios virtual, consulte [Criar conjuntos de relatórios virtuais](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html?lang=pt-BR) na documentação do Adobe Analytics.

Cada VRS possui um identificador exclusivo. Para exibir a ID do conjunto de relatórios principal na interface do usuário do Adobe Mobile Services, acesse a página Gerenciar configurações do aplicativo, seção **[!UICONTROL Informações do aplicativo]**, e clique em **[!UICONTROL Mais detalhes]**.

Na interface do Adobe Mobile Services, você pode usar um VRS para criar um aplicativo e segmentar dados para um grupo específico em sua organização. Dessa forma, por exemplo, um usuário empresarial na Espanha não pode ver os dados relevantes para um usuário empresarial no Japão.

>[!TIP]
>
>Não é possível modificar os valores herdados do conjunto de relatórios principal.

Um VRS é uma definição de segmento do lado do servidor anexada a um conjunto de relatórios principal. Como resultado, não é possível executar a coleta de dados em um VRS, pois o SDK envia ocorrências somente para o conjunto de relatórios principal, que, por sua vez, registra as ocorrências.

## Conjunto de relatórios virtual no Adobe Mobile Services e coleta de dados {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

No Adobe Mobile Services, você pode criar um aplicativo com base em um conjunto de relatórios principal ou virtual. Ao criar um aplicativo com base em um conjunto de relatórios virtual, recomendamos que você alinhe o segmento do VRS com a definição do aplicativo.

>[!TIP]
>
>Certificações por push são anexadas no nível do aplicativo, na interface do usuário do Mobile Services.

Para garantir que suas mensagens de push sejam enviadas corretamente, o segmento de público-alvo deve estar corretamente definido. Para obter mais informações, consulte [Público: definir e configurar os segmentos de público para mensagens por push](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Noções básicas sobre fusos horários {#section_498E1EED22D741C3BDED44F01FACA72A}

A propriedade do fuso horário na página Gerenciar configurações do aplicativo é diferente da propriedade do fuso horário que você usa para criar o VRS no Adobe Analytics. A propriedade na página Gerenciar configurações do aplicativo é herdada do conjunto de relatórios principal, que é usado para enviar dados para o Adobe Analytics. A propriedade especificada ao criar o VRS no Adobe Analytics é usada para exibir os relatórios na interface do usuário do Mobile Services e deve ser diferente do conjunto de relatórios principal.

## Selecionar um conjunto de relatórios virtual na interface do usuário do Mobile Services {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

Para usar um VRS ao criar um aplicativo, selecione o VRS na lista suspensa **[!UICONTROL Conjunto de relatórios]** na página Informações do aplicativo. Esta lista contém conjuntos de relatórios principais e virtuais.

>[!IMPORTANT]
>
>Para selecionar um VRS na lista, localize uma opção com o ponto azul e a convenção de nomenclatura `vrs_` *`<company_name>`*`_`*`<unique name>`*  .

## Propriedades do conjunto de relatórios virtual {#section_20ECE6243F664C4FB4347ADB4FF0458A}

Estas são as propriedades de VRSs:

>[!TIP]
>
>As propriedades somente leitura são herdadas do conjunto de relatórios principal.

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
| `analytics.timezone` | Sim | Sim, ao criar o aplicativo pela primeira vez. | Essa propriedade de fuso horário é usada para enviar dados ao Adobe Analytics e é diferente da propriedade de fuso horário definida quando um VRS é criado. |
| `analytics.timezoneOffset` | Sim | Não |  |
| `analytics.referrerTimeout` | Não | Sim |  |
| `analytics.backdateSessionInfo` | Sim | Sim |  |

## Informações adicionais  {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

Veja a seguir algumas informações adicionais sobre conjuntos de relatórios virtuais:

* Para obter mais informações sobre VRSs, consulte [Visão geral dos conjuntos de relatórios virtuais](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-about.html?lang=pt-BR).
* Para obter mais informações sobre o planejamento de uma implementação de VRS, consulte [Fluxo de trabalho do conjunto de relatórios virtual](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).
