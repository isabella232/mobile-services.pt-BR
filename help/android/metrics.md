---
description: Estas são as métricas e as dimensões que podem ser medidas automaticamente pela biblioteca móvel após a implementação do ciclo de vida, e um link para solucionar problemas de dados do ciclo de vida.
keywords: android;library;mobile;sdk
seo-description: Estas são as métricas e as dimensões que podem ser medidas automaticamente pela biblioteca móvel após a implementação do ciclo de vida, e um link para solucionar problemas de dados do ciclo de vida.
seo-title: Medições de ciclo de vida
solution: Marketing Cloud,Analytics
title: Medições de ciclo de vida
topic: Desenvolvedor e implementação
uuid: a8f3ebac-be3b-4948-82bb-105d46cfff6d
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Lifecycle metrics{#lifecycle-metrics}

Esta seção fornece informações sobre as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel, após a implementação do ciclo de vida, e um link para solucionar problemas de dados do ciclo de vida. Para obter mais informações sobre solução de problemas, acesse [Solução de problemas de dados](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html)do ciclo de vida.

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Quando configuradas, as medições de ciclo de vida são enviadas em parâmetros de dados de contexto ao Analytics, nos parâmetros para o Target com cada chamada mbox e como um sinal ao gerenciamento de público-alvo. O Analytics e o Target usam o mesmo formato, enquanto que o gerenciamento de público-alvo usa um prefixo diferente para cada métrica.

For Analytics, the context data that is sent with each lifecycle tracking call is automatically captured in and reported on by using the metric or dimension, and the exceptions are noted.

### Métricas

* **Primeiras inicializações**

   Disparado na primeira execução após a instalação ou reinstalação.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.InstallEvent`
   * Audience Manager Signal: `c_a_InstallEvent`

* **Atualizações**

   Disparado na primeira execução após uma atualização ou quando o número da versão é alterado.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.UpgradeEvent`
   * Audience Manager Signal: `c_a_UpgradeEvent`

* **Usuários envolvidos diariamente**

   Disparado quando o aplicativo é utilizado em um dia específico.

   >[!IMPORTANT]
   >
   >Essa métrica não é armazenada automaticamente em uma métrica do Analytics. Você deve criar uma regra de processamento que defina um evento personalizado para capturar essa métrica.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.DailyEngUserEvent`
   * Audience Manager Signal: `c_a_DailyEngUserEvent`

* **Usuários envolvidos mensalmente**

   Disparado quando o aplicativo é utilizado durante um mês específico.

   >[!IMPORTANT]
   >
   >This metric is not automatically stored in an Analytics metric. Você deve criar uma regra de processamento que defina um evento personalizado para capturar essa métrica.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.MonthlyEngUserEvent`
   * Audience Manager Signal: `c_a_MonthlyEngUserEvent`

* **Inicializações**

   Disparado a cada execução, incluindo falhas e instalações. Também pode ser disparado em um resumo a partir do plano de fundo quando o tempo limite da sessão de ciclo de vida for excedido.

   >[!IMPORTANT]
   >
   >Essa métrica não é armazenada automaticamente em uma métrica do Analytics. Você deve criar uma regra de processamento que defina um evento personalizado para capturar essa métrica.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.LaunchEvent`
   * Audience Manager Signal: `c_a_LaunchEvent`

* **Falhas**

   Disparado quando o aplicativo não estiver em segundo plano antes do fechamento. O evento é enviado quando o aplicativo é inicializado após a falha.  O relatório de falha do Adobe Mobile não implementa um gerenciador de exceção global não detectado.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.CrashEvent`
   * Audience Manager Signal: `c_a_CrashEvent`

* **Duração da sessão anterior**

   Indica o número de segundos que uma sessão anterior do aplicativo durou com base no tempo em que o aplicativo ficou aberto e no primeiro plano.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.PrevSessionLength`
   * Audience Manager Signal: `c_a_PrevSessionLength`


### Dimensões

* **Data de instalação**

   Data do início após instalação. O formato da data é MM/DD/AAAA.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **ID do aplicativo**

   Stores the application name and version in the `[AppName] [BundleVersion]` format. Um exemplo desse formato é `myapp 1.1`.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **Número de Lançamento**

   Número de vezes em que o aplicativo foi iniciado ou trazido para o plano de fundo.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **Dias desde a primeira visita**

   Número de dias desde a primeira execução.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **Dias desde a última visita**

   Número de dias desde a última utilização.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **Hora do dia**

   Mede a hora em que o aplicativo foi iniciado.  Essa métrica usa o formato numérico de 24 horas e é usada para partir o tempo de forma a determinar as horas de pico de uso.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **Dias da semana**

   Número do dia da semana quando o aplicativo foi iniciado.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **Versão do sistema operacional**

   A versão do SO.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **Dias desde a última atualização**

   Número de dias desde que o número de versão do aplicativo foi alterado.

   >[!IMPORTANT]
   >
   >Essa métrica não é armazenada automaticamente em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **Inicializações desde a última atualização**

   Número de inicializações desde que o número de versão do aplicativo foi alterado.

   >[!IMPORTANT]
   >
   >Essa métrica não é armazenada automaticamente em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **Nome do dispositivo**

   Armazena o nome do dispositivo.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **Nome da operadora**

   Armazena o nome do servidor de serviços para dispositivos móveis, conforme fornecido pelo dispositivo.  Importante: essa métrica não é automaticamente armazenada em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

   >[!IMPORTANT]
   >
   >Essa métrica não é armazenada automaticamente em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **Resolução**

   Largura x altura em pixels reais.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.Resolution`
   * Audience Manager: `c_a_Resolution`

## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

As seguintes métricas e dimensões são capturadas nas variáveis da solução móvel pelo método listado na coluna **Descrição**.

### Métricas

* **Tempo da ação total**

   Populated by `trackTimedAction` methods.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.action.time.total`
   * Característica do Audience Manager: `c_a_action_time_total`

* **Tempo da ação no aplicativo**

   Populated by `trackTimedAction` methods.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.action.time.inapp`
   * Característica do Audience Manager: `c_a_action_time_inapp`

* **Valor de tempo de vida (evento)**

   Populated by `trackLifetimeValue` methods.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.ltv.amount`
   * Característica do Audience Manager: `c_a_ltv_amount`

### Dimensões

* **Localização (abaixo de 10 km)**

   Populated by `trackLocation` methods.

   * Parâmetros de Destino/Dados de Contexto do Analytics:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Características do Audience Manager:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Localização (abaixo de 100 m)**

   Preenchido pelos métodos trackLocation.

   * Parâmetros de Destino/Dados de Contexto do Analytics:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Características do Audience Manager:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Localização (abaixo de 1 m)**

   Preenchido pelos métodos trackLocation.

   * Parâmetros de Destino/Dados de Contexto do Analytics:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Características do Audience Manager:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nome do ponto de interesse**

   Preenchido pelos métodos trackLocation quando o dispositivo está dentro de um POI definido.

   * Analytics Context Data/Target Parameters: `a.loc.poi`
   * Característica do Audience Manager: `c_a_loc_poi`

* **Distância até o centro do ponto de interesse**

   Preenchido pelos métodos trackLocation quando o dispositivo está dentro de um POI definido.

   * Analytics Context Data/Target Parameters: `a.loc.dist`
   * Audience Manager Trait: `c_a_loc_dist`

* **Valor de tempo de vida (variável de conversão)**

   Preenchido pelos métodos trackLifetimeValue.

   * Analytics Context Data/Target Parameters: `a.ltv.amount`
   * Audience Manager Trait: `c_a_ltv_amount`

* **Código de acompanhamento**

   Preenchida pela Aquisição de aplicativos móveis e gerado automaticamente pelo Adobe Mobile Services.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.trackingcode`
   * Audience Manager Trait: `c_a_referrer_campaign_trackingcode`

* ** Campaign

   Nome da campanha, também armazenado na variável da campanha. Preenchido pela Aquisição do dispositivo móvel.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.name`
   * Audience Manager Trait: `c_a_referrer_campaign_name`

* **Conteúdo da campanha**

   O nome ou ID do conteúdo que exibiu o link. Preenchido pela Aquisição do dispositivo móvel.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.content`
   * Audience Manager Trait: `c_a_referrer_campaign_content`

* **Meio da campanha**

   Meio de marketing, como banner ou email. Preenchido pela Aquisição do dispositivo móvel.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.medium`
   * Audience Manager Trait: `c_a_referrer_campaign_medium`

* **Fonte da campanha**

   Referenciador original, como boletins informativos ou uma rede social. Preenchido pela Aquisição do dispositivo móvel.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.source`
   * Audience Manager Trait: `c_a_referrer_campaign_source`

* **Termo da campanha**

   Palavras-chave pagas ou outros termos que você deseja rastrear com essa aquisição. Preenchido pela Aquisição do dispositivo móvel.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.term`
   * Audience Manager Trait: `c_a_referrer_campaign_term`
