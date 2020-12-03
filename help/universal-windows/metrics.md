---
description: Lista as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel.
keywords: android;library;mobile;sdk
seo-description: Lista as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel.
seo-title: Medições de ciclo de vida
solution: Experience Cloud,Analytics
title: Medições de ciclo de vida
topic: Developer and implementation
uuid: f958c3ef-1d79-4b30-8966-ef74bd48a5d6
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 83%

---


# Métricas de ciclo de vida {#lifecycle-metrics}

Lista as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel.

Para obter mais informações, consulte [Solução de problemas de dados](https://helpx.adobe.com/br/analytics/kb/troubleshoot-lifecycle-data.html)do ciclo de vida.


## Métricas de ciclo de vida e dimensões {#section_78F036C4296F4BA3A47C2044F79C86C1}

Quando configuradas, as métricas de ciclo de vida são enviadas em parâmetros de dados de contexto para o Analytics, em parâmetros para o Target com cada chamada de mbox e como um sinal para gerenciamento de público alvo. O Analytics e o Target usam o mesmo formato, enquanto o gerenciamento de público-alvo usa um prefixo diferente para cada métrica.

Para o Analytics, os dados de contexto enviados com cada chamada de rastreamento de ciclo de vida são capturados automaticamente e reportados usando a métrica ou a dimensão. As exceções são observadas no conteúdo.

## Métricas

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

   >[!IMPORTANT]
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

   * Parâmetros do Target/Dados de contexto do Analytics: `a.CrashEvent`
   * Sinal do Audience Manager: `c_a_CrashEvent`

* **Duração da sessão anterior**

   Indica o número de segundos que uma sessão anterior do aplicativo durou com base no tempo em que o aplicativo ficou aberto e no primeiro plano.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.PrevSessionLength`
   * Sinal do Audience Manager: `c_a_PrevSessionLength`


## Dimensões

* **Data de instalação**

   Data do início após instalação. O formato de data é `MM/DD/YYYY`.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.InstallDate`
   * Sinal do Audience Manager: `c_a_InstallDate`

* **ID do aplicativo**

   Armazena o nome e a versão do aplicativo no formato `[AppName] [BundleVersion]`. Um exemplo desse formato é `myapp 1.1`.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.AppID`
   * Sinal do Audience Manager: `c_a_AppID`

* **Número de Lançamento**

   Número de vezes em que o aplicativo foi iniciado ou trazido para o plano de fundo.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.Launches`
   * Sinal do Audience Manager: `c_a_Launches`

* **Dias desde a primeira visita**

   Número de dias desde a primeira execução.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.DaysSinceFirstUse`
   * Sinal do Audience Manager: `c_a_DaysSinceFirstUse`

* **Dias desde a última visita**

   Número de dias desde a última utilização.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.DaysSinceLastUse`
   * Sinal do Audience Manager: `c_a_DaysSinceLastUse`

* **Hora do dia**

   Mede a hora em que o aplicativo foi iniciado. Essa métrica usa o formato numérico de 24 horas e é usada para partir o tempo de forma a determinar as horas de pico de uso.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.HourOfDay`
   * Sinal do Audience Manager: `c_a_HourOfDay`

* **Dias da semana**

   Número do dia da semana quando o aplicativo foi iniciado.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.DayOfWeek`
   * Sinal do Audience Manager: `c_a_DayOfWeek`

* **Versão do sistema operacional**

   A versão do sistema operacional.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.OSVersion`
   * Sinal do Audience Manager: `c_a_OSVersion`

* **Dias desde a última atualização**

   Número de dias desde que o número de versão do aplicativo foi alterado.

   >[!IMPORTANT]
   >
   >Essa métrica não é automaticamente armazenada em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.DaysSinceLastUpgrade`
   * Sinal do Audience Manager: `c_a_DaysSinceLastUpgrade`

* **Inicializações desde a última atualização**

   Número de inicializações desde que o número de versão do aplicativo foi alterado.

   >[!IMPORTANT]
   >
   >Essa métrica não é automaticamente armazenada em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.LaunchesSinceUpgrade`
   * Sinal do Audience Manager: `c_a_LaunchesSinceUpgrade`

* **Nome do dispositivo**

   Armazena o nome do dispositivo.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.DeviceName`
   * Sinal do Audience Manager: `c_a_DeviceName`

* **Nome da operadora**

   Armazena o nome do servidor de serviços para dispositivos móveis, conforme fornecido pelo dispositivo.

   >[!IMPORTANT]
   >
   >Essa métrica não é automaticamente armazenada em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.CarrierName`
   * Sinal do Audience Manager: `c_a_CarrierName`

* **Resolução**

   Largura x altura em pixels reais.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.Resolution`
   * Sinal do Audience Manager: `c_a_Resolution`


## Métricas e dimensões móveis adicionais {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

As seguintes métricas e dimensões são capturadas nas variáveis de solução móvel pelo seguinte método:

### Métricas

* **Tempo da ação total**

   Preenchido pelos métodos `trackTimedAction`.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.action.time.total`
   * Sinal do Audience Manager: `c_a_action_time_total`

* **Tempo da ação no aplicativo**

   Preenchido pelos métodos `trackTimedAction`.
   * Parâmetro do Target/Dados de contexto do Analytics: `a.action.time.inapp`
   * Sinal do Audience Manager: `c_a_action_time_inapp`

* **Valor de tempo de vida (evento)**

   Preenchido pelos métodos `trackLifetimeValue`.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.ltv.amount`
   * Sinal do Audience Manager: `c_a_ltv_amount`

### Dimensões

* **Localização (abaixo de 10 km)**

   Preenchido pelos métodos `trackLocation`.

   * Parâmetro(s) de Público alvo/Dados de contexto do Analytics:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Manager:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Localização (abaixo de 100 m)**

   Preenchido pelos métodos `trackLocation`.

   * Parâmetro(s) de Público alvo/Dados de contexto do Analytics:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Localização (abaixo de 1 m)**

   Preenchido pelos métodos `trackLocation`.

   * Parâmetro(s) de Público alvo/Dados de contexto do Analytics:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nome do ponto de interesse**

   Populated by `trackLocation` methods when device is in a defined POI.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.loc.poi`
   * Audience Manager trait: `c_a_loc_poi`

* **Distância até o centro do ponto de interesse**

   Populated by `trackLocation` methods when device is within a defined POI.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.loc.dist`
   * Audience Manager trait: `c_a_loc_dist`

* **Valor de tempo de vida (variável de conversão)**

   Preenchido pelos métodos `trackLifetimeValue`.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.ltv.amount`
   * Audience Manager trait: `c_a_ltv_amount`
