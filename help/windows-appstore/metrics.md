---
description: Lista as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel.
keywords: android;biblioteca;móvel;sdk
solution: Experience Cloud Services,Analytics
title: Medições de ciclo de vida
topic-fix: Developer and implementation
uuid: c483271f-f620-46f4-aad8-d5f02d763f7d
exl-id: a1e4eeca-8b8f-47ca-a489-acc338238c42
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 64%

---

# Medições de ciclo de vida{#lifecycle-metrics}

Lista as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel.

Para obter mais informações, consulte [Solução de problemas de dados do ciclo de vida](https://helpx.adobe.com/br/analytics/kb/troubleshoot-lifecycle-data.html).

## Medições e dimensões de ciclo de vida {#section_78F036C4296F4BA3A47C2044F79C86C1}

Quando configuradas, as medições de ciclo de vida são enviadas em parâmetros de dados de contexto para o Analytics, em parâmetros para o Target com cada chamada de mbox e como um sinal para o Audience Manager. O Analytics e o Target usam o mesmo formato, e o Audience Manager usa um prefixo diferente para cada métrica.

Para o Analytics, os dados de contexto que são enviados com cada chamada de rastreamento do ciclo de vida são automaticamente capturados e reportados usando a métrica ou dimensão listada abaixo, e as exceções são anotadas.

### Métricas

* **Primeiras inicializações**

   Disparado na primeira execução após a instalação ou reinstalação.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.InstallEvent`
   * Sinal do Audience Manager: `c_a_InstallEvent`

* **Atualizações**

   Disparado na primeira execução após uma atualização ou quando o número da versão é alterado.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.UpgradeEvent`
   * Sinal do Audience Manager: `c_a_UpgradeEvent`

* **Usuários envolvidos diariamente**

   Disparado quando o aplicativo é utilizado em um dia específico.

   >[!TIP]
   >
   >Essa métrica não é automaticamente armazenada em uma métrica do Analytics. Você deve criar uma regra de processamento que defina um evento personalizado para capturar essa métrica.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.DailyEngUserEvent`
   * Sinal do Audience Manager: `c_a_DailyEngUserEvent`

* **Usuários envolvidos mensalmente**

   Disparado quando o aplicativo é utilizado durante um mês específico.

   >[!IMPORTANT]
   >
   >Essa métrica não é automaticamente armazenada em uma métrica do Analytics. Você deve criar uma regra de processamento que defina um evento personalizado para capturar essa métrica.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.MonthlyEngUserEvent`
   * Sinal do Audience Manager: `c_a_MonthlyEngUserEvent`

* **Inicializações**

   Acionadas a cada execução, incluindo falhas e instalações. Também é acionado em um resumo do plano de fundo quando o tempo limite da sessão do ciclo de vida é excedido.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.LaunchEvent`
   * Sinal do Audience Manager: `c_a_LaunchEvent`

* **Falhas**

   Disparado quando o aplicativo não estiver em segundo plano antes do fechamento. O evento é enviado quando o aplicativo é inicializado após a falha. O relatório de falha do Adobe Mobile não implementa um gerenciador de exceção global não detectado.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.CrashEvent`
   * Sinal do Audience Manager: `c_a_CrashEvent`

* **Duração da sessão anterior**

   Indica o número de segundos que uma sessão anterior do aplicativo durou com base no tempo em que o aplicativo ficou aberto e no primeiro plano.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.PrevSessionLength`
   * Sinal do Audience Manager: `c_a_PrevSessionLength`

### Dimensões

* **Data de instalação**

   Data do início após instalação. O formato de data é `MM/DD/YYYY`.

   * Target/Dados de contexto do Analytics: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **ID do aplicativo**

   Armazena o nome e a versão do aplicativo no formato `[AppName] [BundleVersion]`. Um exemplo desse formato é `myapp 1.1`.

   * Target/Dados de contexto do Analytics: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **Número de Lançamento**

   Número de vezes em que o aplicativo foi iniciado ou trazido para o plano de fundo.

   * Target/Dados de contexto do Analytics: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **Dias desde a primeira visita**

   Número de dias desde a primeira execução.

   * Target/Dados de contexto do Analytics: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **Dias desde a última visita**

   Número de dias desde a última utilização.

   * Target/Dados de contexto do Analytics: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **Hora do dia**

   Mede a hora em que o aplicativo foi iniciado. Essa métrica usa o formato numérico de 24 horas e é usada para partir o tempo de forma a determinar as horas de pico de uso.

   * Target/Dados de contexto do Analytics: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **Dias da semana**

   Número do dia da semana quando o aplicativo foi iniciado.

   * Target/Dados de contexto do Analytics: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **Versão do sistema operacional**

   A versão do sistema operacional.

   * Target/Dados de contexto do Analytics: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **Dias desde a última atualização**

   Número de dias desde que o número de versão do aplicativo foi alterado.

   >[!IMPORTANT]
   >
   >Essa métrica não é automaticamente armazenada em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

   * Target/Dados de contexto do Analytics: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **Inicializações desde a última atualização**

   Número de inicializações desde que o número de versão do aplicativo foi alterado.

   >[!IMPORTANT]
   >
   >Essa métrica não é automaticamente armazenada em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

   * Target/Dados de contexto do Analytics: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **Nome do dispositivo**

   Armazena o nome do dispositivo.

   * Target/Dados de contexto do Analytics: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **Nome da operadora**

   Armazena o nome do servidor de serviços para dispositivos móveis, conforme fornecido pelo dispositivo.

   >[!IMPORTANT]
   >
   >Essa métrica não é automaticamente armazenada em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

   * Target/Dados de contexto do Analytics: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **Resolução**

   Largura x altura em pixels reais.

   * Target/Dados de contexto do Analytics: `a.Resolution`
   * Audience Manager: `c_a_Resolution`


## Métricas e dimensões móveis adicionais {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

As métricas e dimensões a seguir são capturadas nas variáveis da solução móvel pelos métodos listados na descrição.

### Métricas

* **Tempo da ação total**

   Preenchido pelos métodos `trackTimedAction`.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.action.time.total`
   * Audience Manager: `c_a_action_time_total`

* **Tempo da ação no aplicativo**

   Preenchido pelos métodos `trackTimedAction`.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.action.time.inapp`
   * Audience Manager: `c_a_action_time_inapp`

* **Valor de tempo de vida (evento)**

   Preenchido pelos métodos `trackLifetimeValue`.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.ltv.amount`
   * Audience Manager: `c_a_ltv_amount`

## Dimensões

* **Localização (abaixo de 10 km)**

   Preenchido pelos métodos `trackLocation`.

   * Parâmetro do Target/Dados de contexto do Analytics:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Manager:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Localização (abaixo de 100 m)**

   Preenchido pelos métodos `trackLocation`.

   * Parâmetro do Target/Dados de contexto do Analytics:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Localização (abaixo de 1 m)**

   Preenchido pelos métodos `trackLocation`.

   * Parâmetro do Target/Dados de contexto do Analytics:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nome do ponto de interesse**

   Preenchido por `trackLocation` métodos quando o dispositivo está dentro de um POI definido.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.loc.poi`
   * Audience Manager: `c_a_loc_poi`

* **Distância até o centro do ponto de interesse**

   Preenchido por `trackLocation` métodos quando o dispositivo está dentro de um POI definido.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.loc.dist`
   * Audience Manager: `c_a_loc_dist`

* **Valor de tempo de vida (variável de conversão)**

   Preenchido pelos métodos `trackLifetimeValue`.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.ltv.amount`
   * Audience Manager: `c_a_ltv_amount`
