---
description: Estas são as métricas e as dimensões que podem ser medidas automaticamente pela biblioteca móvel após a implementação do ciclo de vida, e um link para solucionar problemas de dados do ciclo de vida.
keywords: android;biblioteca;móvel;sdk
solution: Experience Cloud Services,Analytics
title: Medições de ciclo de vida
topic-fix: Developer and implementation
uuid: 5a371f11-6521-410f-a01f-fc3b285b050f
exl-id: d7436411-65bd-4cf7-ae3e-cec829a7690a
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 77%

---

# Medições de ciclo de vida {#lifecycle-metrics}

Estas são as métricas e as dimensões que podem ser medidas automaticamente pela biblioteca móvel após a implementação do ciclo de vida, e um link para solucionar problemas de dados do ciclo de vida.

Para obter mais informações, acesse a Base de conhecimento em [Solução de problemas de dados do ciclo de vida](https://helpx.adobe.com/br/analytics/kb/troubleshoot-lifecycle-data.html).

## Medições e dimensões de ciclo de vida {#section_78F036C4296F4BA3A47C2044F79C86C1}

Quando configuradas, as métricas de ciclo de vida são enviadas em parâmetros de dados de contexto para o Analytics, em parâmetros para o Target com cada chamada de mbox e como um sinal para gerenciamento de público alvo. O Analytics e o Target usam o mesmo formato, enquanto o gerenciamento de público-alvo usa um prefixo diferente para cada métrica.

Para o Analytics, os dados de contexto enviados com cada chamada de rastreamento do ciclo de vida são automaticamente capturados e reportados usando a métrica ou a dimensão.

### Métricas

* **a.media.name**

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

   Disparado quando o aplicativo é utilizado durante um mês específico.  >>>>

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

   * Parâmetro do Target/Dados de contexto do Analytics: `a.InstallDate`
   * Sinal do Audience Manager: `c_a_InstallDate`

* **ID do aplicativo**

   Armazena o nome e a versão do aplicativo no seguinte formato:
   `[AppName] [BundleVersion]`.

   Um exemplo desse formato é `myapp 1.1`.

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

   A versão do SO.

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

As métricas e dimensões a seguir são capturadas em variáveis de solução móvel pelo método listado.

* **Localização (abaixo de 10 km)**

   Preenchido pelos métodos `trackLocation`.

   * Parâmetro do Target/Dados de contexto do Analytics:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Característica do Audience Management:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Localização (abaixo de 100 m)**

   Preenchido pelos métodos `trackLocation`.

   * Parâmetro do Target/Dados de contexto do Analytics:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Característica do Audience Management:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Localização (abaixo de 1 m)**

   Preenchido pelos métodos `trackLocation`.

   * Parâmetro do Target/Dados de contexto do Analytics:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Característica do Audience Management:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nome do ponto de interesse**

   Preenchido por `trackLocation` métodos quando o dispositivo está dentro de um POI definido.

   * Parâmetro do Target/Dados de contexto do Analytics:

      * `a.loc.poi`
   * Característica do Audience Management:

      * `c_a_loc_poi`


* **Distância até o centro do ponto de interesse**

   Preenchido por `trackLocation` métodos quando o dispositivo está dentro de um POI definido.

   * Parâmetro do Target/Dados de contexto do Analytics:

      * `a.loc.dist`
   * Característica do Audience Management:

      * `c_a_loc_dist`
