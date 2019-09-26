---
description: As tabelas a seguir listam as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel após a implementação do ciclo de vida.
seo-description: As tabelas a seguir listam as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel após a implementação do ciclo de vida.
seo-title: Medições de ciclo de vida
solution: Marketing Cloud,Analytics
title: Medições de ciclo de vida
topic: Desenvolvedor e implementação
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
translation-type: tm+mt
source-git-commit: a6608bf4d36a6fb6aca00f50cc058c09dbd931b1

---


# Lifecycle metrics {#lifecycle-metrics}

Here are the metrics and dimensions that can be automatically measured by the mobile library after lifecycle is implemented.

## New Adobe Experience Platform Mobile SDK Release

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* To get started, go to [Experience Platform Launch](https://launch.adobe.com/).
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Após as medições de ciclo de vida serem configuradas, elas são enviadas nos parâmetros de dados de contexto ao Analytics, nos parâmetros ao Target com cada chamada da mbox e como um sinal ao Audience Manager. O Analytics e o Target usam o mesmo formato, enquanto o Audience Manager usa um prefixo diferente para cada métrica.

Para o Analytics, os dados de contexto que são enviados com cada chamada de rastreamento do ciclo de vida são automaticamente capturados e reportados usando a métrica ou a dimensão listada na primeira coluna.

>[!TIP]
>
>As exceções são fornecidas na descrição.

### Métricas

* **Primeiras inicializações**

   Disparado na primeira execução após a instalação ou reinstalação.

   * Analytics Context Data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **Atualizações**

   Disparado na primeira execução após a atualização ou quando o número da versão se altera.

   * Analytics Context Data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **Usuários envolvidos diariamente**

   Disparado quando o aplicativo é utilizado em um dia específico.

   * Analytics Context Data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **Usuários envolvidos mensalmente**

   Disparado quando o aplicativo é utilizado durante um mês específico.

   * Analytics Context Data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **Inicializações**

   Desencadeado a cada execução, incluindo falhas e instalações. Também disparado quando o aplicativo é retomado do segundo plano após o limite de tempo da sessão de ciclo de vida ser excedido.

   * Analytics Context Data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **Falhas**

   Acionado quando o aplicativo não estiver em segundo plano antes do fechamento. O evento é enviado quando o aplicativo é iniciado novamente após a falha.  O relatório de falha do Adobe Mobile não implementa um gerenciador de exceção global não detectado.

   * Analytics Context Data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **Duração da sessão anterior**

   Informa o número de segundos que uma sessão anterior do aplicativo durou com base no tempo em que o aplicativo ficou aberto e no primeiro plano.

   * Analytics Context Data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> As métricas Usuários *envolvidos* diariamente e Usuários ** envolvidos mensalmente não são armazenadas automaticamente em uma métrica do Analytics. É necessário criar uma regra de processamento que defina um evento personalizado para capturar essas métricas.

#### Dimensões

* **Data de instalação**

   Data do início após instalação.  O formato de data é `MM/DD/YYYY`.

   * Target/Dados de contexto do Analytics: `a.InstallDate`
   * Gerenciamento de público-alvo: `c_a_InstallDate`

* **ID do aplicativo**

   Stores the Application name and version in the `[AppName] [BundleVersion]` format. Por exemplo, `myapp 1.1`.

   * Target/Dados de contexto do Analytics: `a.AppID`
   * Gerenciamento de público-alvo: `c_a_AppID`

* **Número de Lançamento**

   Número de vezes em que o aplicativo foi iniciado ou trazido para o plano de fundo.

   * Target/Dados de contexto do Analytics: `a.Launches`
   * Gerenciamento de público-alvo: `c_a_Launches`

* **Dias desde a primeira visita**

   Número de dias desde a primeira execução.

   * Target/Dados de contexto do Analytics: `a.DaysSinceFirstUse`
   * Gerenciamento de público-alvo: `c_a_DaysSinceFirstUse`

* **Dias desde a última visita**

   Número de dias desde a última utilização.

   * Target/Dados de contexto do Analytics: `a.DaysSinceLastUse`
   * Gerenciamento de público-alvo: `c_a_DaysSinceLastUse`

* **Hora do dia**

   Mede a hora em que o aplicativo foi iniciado e usa o formato numérico de 24 horas. Utilizado para hora do visitante para determinar os tempos de pico de uso.

   * Target/Dados de contexto do Analytics: `a.HourOfDay`
   * Gerenciamento de público-alvo: `c_a_HourOfDay`

* **Dias da semana**

   Número do dia da semana no qual o aplicativo foi iniciado.

   * Target/Dados de contexto do Analytics: `a.DayOfWeek`
   * Gerenciamento de público-alvo: `c_a_DayOfWeek`

* **Versão do sistema operacional**

   Número de dias desde que o número de versão do aplicativo foi alterado.

   * Target/Dados de contexto do Analytics: `a.OSVersion`
   * Gerenciamento de público-alvo: `c_a_OSVersion|OS version`

* **Dias desde a última atualização**

   Dias desde a última atualização.

   * Target/Dados de contexto do Analytics: `a.DaysSinceLastUpgrade`
   * Gerenciamento de público-alvo: `c_a_DaysSinceLastUpgrade`

* **Inicializações desde a última atualização**

   Número de inicializações desde que o número de versão do aplicativo foi alterado.

   * Target/Dados de contexto do Analytics: `a.LaunchesSinceUpgrade`
   * Gerenciamento de público-alvo: `c_a_LaunchesSinceUpgrade`

* **Nome do dispositivo**

   Armazena o nome do dispositivo.  Cadeia de caracteres de dígitos separados por vírgulas que identifica o dispositivo iOS. O primeiro número tipicamente representa a geração do dispositivo e o segundo, versões dos diferentes membros da família do dispositivo. Para obter uma lista de nomes comuns, consulte  Versões do dispositivo iOS.

   * Target/Dados de contexto do Analytics: `a.DeviceName`
   * Gerenciamento de público-alvo: `c_a_DeviceName`

* **Nome da operadora**

   Armazena o nome do servidor de serviços para dispositivos móveis, conforme fornecido pelo dispositivo.

   * Target/Dados de contexto do Analytics: `a.CarrierName`
   * Gerenciamento de público-alvo: `c_a_CarrierName`

* **Resolução**

   Largura x altura em pixels reais.

   * Target/Dados de contexto do Analytics: `a.Resolution`
   * Gerenciamento de público-alvo: `c_a_Resolution`
   >[!IMPORTANT]
   >
   >Os *Dias desde a última atualização*, as *Inicializações desde a última atualização* e as dimensões Nome *da* operadora não são armazenadas automaticamente em uma variável do Analytics. É necessário criar uma regra de processamento para copiar os valores para uma variável do Analytics para geração de relatórios.


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

As métricas e dimensões a seguir são capturadas em variáveis de solução móvel pelo método listado.

### Métricas

* **Tempo da ação total**

   Preenchido pelos métodos trackTimedAction.

   * Analytics Context Data/Target parameter: `a.action.time.total`
   * Audience Management trait: `c_a_action_time_total`

* **Tempo da ação no aplicativo**

   Preenchido pelos métodos trackTimedAction.

   * Analytics Context Data/Target parameter: `a.action.time.inapp`
   * Audience Management trait: `c_a_action_time_inapp`

* **Valor de tempo de vida (evento)**

   Preenchido pelos métodos trackLifetimeValue.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`


### Dimensões

* **Localização (abaixo de 10 km)**

   Populated by `trackLocation` methods.

   * Parâmetro Dados de contexto/Target do Analytics:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Management trait:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Localização (abaixo de 100 m)**

   Preenchido pelos métodos trackLocation.

   * Analytics Context Data/Target parameter:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Management trait:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Localização (abaixo de 1 m)**

   Populated by `trackLocation` methods.

   * Analytics Context Data/Target parameter:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Característica do Gerenciamento de público-alvo:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nome do ponto de interesse**

   Preenchido pelos métodos trackLocation quando o dispositivo está em um POI definido.

   * Analytics Context Data/Target parameter: `a.loc.poi`
   * Audience Management trait: `c_a_loc_poi`

* **Distância até o centro do ponto de interesse**

   Preenchido pelos métodos trackLocation quando o dispositivo está em um POI definido.

   * Analytics Context Data/Target parameter: `a.loc.dist`
   * Audience Management trait: `c_a_loc_dist`

* **Valor de tempo de vida (variável de conversão)**

   Preenchido pelos métodos trackLifetimeValue.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`

* **Código de acompanhamento**

   Preenchido pela Aquisição do dispositivo móvel. Gerado automaticamente pelos Adobe Mobile Services.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.trackingcode`
   * Audience Management trait: `c_a_referrer_campaign_trackingcode`

* **Campaign**

   Nome da campanha, também armazenado na variável da campanha. Preenchido pela Aquisição do dispositivo móvel.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.name`
   * Audience Management trait: `c_a_referrer_campaign_name`

* **Conteúdo da campanha**

   O nome ou ID do conteúdo que exibiu o link. Preenchido pela Aquisição do dispositivo móvel.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.content`
   * Audience Management trait: `c_a_referrer_campaign_content`

* **Meio da campanha**

   Meio de marketing, como banner ou email. Preenchido pela Aquisição do dispositivo móvel.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.medium`
   * Audience Management trait: `c_a_referrer_campaign_medium`

* **Fonte da campanha**

   Referenciador original, como boletins informativos ou redes de mídia social. Preenchido pela Aquisição do dispositivo móvel.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.source`
   * Audience Management trait: `c_a_referrer_campaign_source`

* **Termo da campanha**

   Palavras-chave pagas ou outros termos que você deseja acompanhar com essa aquisição. Preenchido pela Aquisição do dispositivo móvel.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.term`
   * Audience Management trait: `c_a_referrer_campaign_term`
