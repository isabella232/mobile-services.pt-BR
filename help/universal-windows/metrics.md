---
description: Lista as métricas e dimensões que podem ser medidas automaticamente por meio da biblioteca para dispositivos móveis.
keywords: android;library;mobile;sdk
seo-description: Lista as métricas e dimensões que podem ser medidas automaticamente por meio da biblioteca para dispositivos móveis.
seo-title: Medições de ciclo de vida
solution: Marketing Cloud,Analytics
title: Medições de ciclo de vida
topic: Desenvolvedor e implementação
uuid: f958c3ef-1d79-4b30-8966-ef74bd48a5d6
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Lifecycle metrics {#lifecycle-metrics}

Lista as métricas e dimensões que podem ser medidas automaticamente por meio da biblioteca para dispositivos móveis.

Para obter mais informações, consulte [Solução de problemas de dados](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html)do ciclo de vida.


## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Quando configuradas, as medições de ciclo de vida são enviadas em parâmetros de dados de contexto ao Analytics, nos parâmetros para o Target com cada chamada mbox e como um sinal ao gerenciamento de público-alvo. O Analytics e o Target usam o mesmo formato, enquanto que o gerenciamento de público-alvo usa um prefixo diferente para cada métrica.

Para o Analytics, os dados de contexto enviados com cada chamada de rastreamento de ciclo de vida são capturados automaticamente e reportados usando a métrica ou a dimensão. As exceções são observadas no conteúdo.

## Métricas

* **Primeiras inicializações**

   Disparado na primeira execução após a instalação ou reinstalação.

   * Analytics Context Data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **Atualizações**

   Disparado na primeira execução após uma atualização ou quando o número da versão é alterado.

   * Analytics Context Data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **Usuários envolvidos diariamente**

   Disparado quando o aplicativo é utilizado em um dia específico.

   >[!IMPORTANT]
   >
   >Essa métrica não é armazenada automaticamente em uma métrica do Analytics. Você deve criar uma regra de processamento que defina um evento personalizado para capturar essa métrica.

   * Analytics Context Data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **Usuários envolvidos mensalmente**

   Disparado quando o aplicativo é utilizado durante um mês específico.

   >[!IMPORTANT]
   >
   >This metric is not automatically stored in an Analytics metric. Você deve criar uma regra de processamento que defina um evento personalizado para capturar essa métrica.

   * Analytics Context Data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **Inicializações**

   Disparado a cada execução, incluindo falhas e instalações. Também pode ser disparado em um resumo a partir do plano de fundo quando o tempo limite da sessão de ciclo de vida for excedido.

   * Analytics Context Data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **Falhas**

   Disparado quando o aplicativo não estiver em segundo plano antes do fechamento. O evento é enviado quando o aplicativo é inicializado após a falha. O relatório de falha do Adobe Mobile não implementa um gerenciador de exceção global não detectado.

   * Analytics Context Data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **Duração da sessão anterior**

   Indica o número de segundos que uma sessão anterior do aplicativo durou com base no tempo em que o aplicativo ficou aberto e no primeiro plano.

   * Analytics Context Data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`


## Dimensões

* **Data de instalação**

   Data do início após instalação. O formato de data é `MM/DD/YYYY`.

   * Analytics Context Data/Target parameter: `a.InstallDate`
   * Audience Manager signal: `c_a_InstallDate`

* **ID do aplicativo**

   Stores the application name and version in the `[AppName] [BundleVersion]` format. Um exemplo desse formato é `myapp 1.1`.

   * Analytics Context Data/Target parameter: `a.AppID`
   * Audience Manager signal: `c_a_AppID`

* **Número de Lançamento**

   Número de vezes em que o aplicativo foi iniciado ou trazido para o plano de fundo.

   * Analytics Context Data/Target parameter: `a.Launches`
   * Audience Manager signal: `c_a_Launches`

* **Dias desde a primeira visita**

   Número de dias desde a primeira execução.

   * Analytics Context Data/Target parameter: `a.DaysSinceFirstUse`
   * Audience Manager signal: `c_a_DaysSinceFirstUse`

* **Dias desde a última visita**

   Número de dias desde a última utilização.

   * Analytics Context Data/Target parameter: `a.DaysSinceLastUse`
   * Audience Manager signal: `c_a_DaysSinceLastUse`

* **Hora do dia**

   Mede a hora em que o aplicativo foi iniciado. Essa métrica usa o formato numérico de 24 horas e é usada para partir o tempo de forma a determinar as horas de pico de uso.

   * Analytics Context Data/Target parameter: `a.HourOfDay`
   * Audience Manager signal: `c_a_HourOfDay`

* **Dias da semana**

   Número do dia da semana quando o aplicativo foi iniciado.

   * Analytics Context Data/Target parameter: `a.DayOfWeek`
   * Audience Manager signal: `c_a_DayOfWeek`

* **Versão do sistema operacional**

   A versão do SO.

   * Analytics Context Data/Target parameter: `a.OSVersion`
   * Audience Manager signal: `c_a_OSVersion`

* **Dias desde a última atualização**

   Número de dias desde que o número de versão do aplicativo foi alterado.

   >[!IMPORTANT]
   >
   >Essa métrica não é armazenada automaticamente em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

   * Analytics Context Data/Target parameter: `a.DaysSinceLastUpgrade`
   * Audience Manager signal: `c_a_DaysSinceLastUpgrade`

* **Inicializações desde a última atualização**

   Número de inicializações desde que o número de versão do aplicativo foi alterado.

   >[!IMPORTANT]
   >
   >Essa métrica não é armazenada automaticamente em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

   * Analytics Context Data/Target parameter: `a.LaunchesSinceUpgrade`
   * Audience Manager signal: `c_a_LaunchesSinceUpgrade`

* **Nome do dispositivo**

   Armazena o nome do dispositivo.

   * Analytics Context Data/Target parameter: `a.DeviceName`
   * Audience Manager signal: `c_a_DeviceName`

* **Nome da operadora**

   Armazena o nome do servidor de serviços para dispositivos móveis, conforme fornecido pelo dispositivo.

   >[!IMPORTANT]
   >
   >This metric is not automatically stored in an Analytics variable. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

   * Analytics Context Data/Target parameter: `a.CarrierName`
   * Audience Manager signal: `c_a_CarrierName`

* **Resolução**

   Largura x altura em pixels reais.

   * Analytics Context Data/Target parameter: `a.Resolution`
   * Audience Manager signal: `c_a_Resolution`


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

As seguintes métricas e dimensões são capturadas nas variáveis de solução móvel pelo seguinte método:

### Métricas

* **Tempo da ação total**

   Populated by `trackTimedAction` methods.

   * Analytics Context Data/Target parameter: `a.action.time.total`
   * Audience Manager signal: `c_a_action_time_total`

* **Tempo da ação no aplicativo**

   Populated by `trackTimedAction` methods.
   * Analytics Context Data/Target parameter: `a.action.time.inapp`
   * Audience Manager signal: `c_a_action_time_inapp`

* **Valor de tempo de vida (evento)**

   Populated by `trackLifetimeValue` methods.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Manager signal: `c_a_ltv_amount`

### Dimensões

* **Localização (abaixo de 10 km)**

   Populated by `trackLocation` methods.

   * Parâmetro(s) Dados de contexto/Target do Analytics:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Características do Audience Manager:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Localização (abaixo de 100 m)**

   Populated by `trackLocation` methods.

   * Parâmetro(s) Dados de contexto/Target do Analytics:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Características do Audience Manager:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Localização (abaixo de 1 m)**

   Populated by `trackLocation` methods.

   * Parâmetro(s) Dados de contexto/Target do Analytics:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Características do Audience Manager:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nome do ponto de interesse**

   Preenchido pelos métodos `trackLocation` quando o dispositivo está em um POI definido.

   * Analytics Context Data/Target parameter: `a.loc.poi`
   * Característica do Audience Manager: `c_a_loc_poi`

* **Distância até o centro do ponto de interesse**

   Preenchido pelos métodos `trackLocation` quando o dispositivo está dentro de um POI definido.

   * Analytics Context Data/Target parameter: `a.loc.dist`
   * Característica do Audience Manager: `c_a_loc_dist`

* **Valor de tempo de vida (variável de conversão)**

   Populated by `trackLifetimeValue` methods.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Característica do Audience Manager: `c_a_ltv_amount`
