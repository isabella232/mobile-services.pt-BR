---
description: Estas tabelas listam as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel após a implementação do ciclo de vida.
seo-description: Estas tabelas listam as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel após a implementação do ciclo de vida.
seo-title: Medições de ciclo de vida
solution: Experience Cloud,Analytics
title: Medições de ciclo de vida
topic: Developer and implementation
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '1108'
ht-degree: 100%

---


# Métricas de ciclo de vida {#lifecycle-metrics}

Estas tabelas listam as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel após a implementação do ciclo de vida.

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para obter a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o [Experience Platform Launch](https://launch.adobe.com/).
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Medições e dimensões de ciclo de vida {#section_78F036C4296F4BA3A47C2044F79C86C1}

Após as medições de ciclo de vida serem configuradas, elas são enviadas nos parâmetros de dados de contexto ao Analytics, nos parâmetros ao Target com cada chamada da mbox e como um sinal ao Audience Manager. O Analytics e o Target usam o mesmo formato, enquanto o Audience Manager usa um prefixo diferente para cada métrica.

Para o Analytics, os dados de contexto que são enviados com cada chamada de rastreamento do ciclo de vida são automaticamente capturados e reportados usando a métrica ou a dimensão listada na primeira coluna.

>[!TIP]
>
>As exceções são fornecidas na descrição.

### Métricas

* **Primeiras inicializações**

   Disparado na primeira execução após a instalação ou reinstalação.

   * Parâmetro do Target/Dados de contexto do Analytics: `a.InstallEvent`
   * Sinal do Audience Manager: `c_a_InstallEvent`

* **Atualizações**

   Disparado na primeira execução após a atualização ou quando o número da versão se altera.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.UpgradeEvent`
   * Sinal do Audience Manager: `c_a_UpgradeEvent`

* **Usuários envolvidos diariamente**

   Disparado quando o aplicativo é utilizado em um dia específico.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.DailyEngUserEvent`
   * Sinal do Audience Manager: `c_a_DailyEngUserEvent`

* **Usuários envolvidos mensalmente**

   Disparado quando o aplicativo é utilizado durante um mês específico.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.MonthlyEngUserEvent`
   * Sinal do Audience Manager: `c_a_MonthlyEngUserEvent`

* **Inicializações**

   Desencadeado a cada execução, incluindo falhas e instalações. Também acionado quando o aplicativo é retomado do plano de fundo depois que o tempo limite da sessão do ciclo de vida é excedido.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.LaunchEvent`
   * Sinal do Audience Manager: `c_a_LaunchEvent`

* **Falhas**

   Acionado quando o aplicativo não estiver em segundo plano antes do fechamento. O evento é enviado quando o aplicativo é iniciado novamente após a falha.  O relatório de falha do Adobe Mobile não implementa um gerenciador de exceção global não detectado.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.CrashEvent`
   * Sinal do Audience Manager: `c_a_CrashEvent`

* **Duração da sessão anterior**

   Informa o número de segundos que uma sessão anterior do aplicativo durou com base no tempo em que o aplicativo ficou aberto e no primeiro plano.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.PrevSessionLength`
   * Sinal do Audience Manager: `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> As métricas dos *Usuários envolvidos diariamente* e *Usuários envolvidos mensalmente* não são armazenadas automaticamente em uma métrica do Analytics. Você deve criar uma regra de processamento que defina um evento personalizado para capturar essa métrica.

#### Dimensões

* **Data de instalação**

   Data do início após instalação.  O formato de data é `MM/DD/YYYY`.

   * Target/Dados de contexto do Analytics: `a.InstallDate`
   * Gerenciamento de público-alvo: `c_a_InstallDate`

* **ID do aplicativo**

   Armazena o nome e a versão do aplicativo no formato `[AppName] [BundleVersion]`. Por exemplo, `myapp 1.1`.

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

   Mede a hora em que o aplicativo foi inicializado e usa o formato numérico de 24 horas. Utilizado para hora do visitante para determinar os tempos de pico de uso.

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

   Armazena o nome do dispositivo.  String de dois dígitos separada por vírgulas que identifica o dispositivo iOS. O primeiro número representa a geração do dispositivo e o segundo representa versões dos diferentes membros da família do dispositivo. Para obter uma lista de nomes comuns, consulte    as versões do dispositivo iOS.

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
   >Os *Dias desde a última atualização*, as *Inicializações desde a última atualização* e as dimensões do *Nome da operadora* não são armazenadas automaticamente em uma variável do Analytics. Para os relatórios, é necessário criar uma regra de processamento para copiar os valores para uma variável do Analytics.


## Métricas e dimensões móveis adicionais {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

As métricas e dimensões a seguir são capturadas em variáveis de solução móvel pelo método listado.

### Métricas

* **Tempo da ação total**

   Preenchido pelos métodos trackTimedAction.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.action.time.total`
   * Característica do Audience Management: `c_a_action_time_total`

* **Tempo da ação no aplicativo**

   Preenchido pelos métodos trackTimedAction.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.action.time.inapp`
   * Característica do Audience Management: `c_a_action_time_inapp`

* **Valor vitalício (evento)**

   Preenchido pelos métodos trackLifetimeValue.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.ltv.amount`
   * Característica do Audience Management: `c_a_ltv_amount`


### Dimensões

* **Localização (abaixo de 10 km)**

   Preenchido pelos métodos `trackLocation`.

   * Parâmetros do Target/Dados de contexto do Analytics:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Característica do Audience Management:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Localização (abaixo de 100 m)**

   Preenchido pelos métodos trackLocation.

   * Parâmetros do Target/Dados de contexto do Analytics:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Característica do Audience Management:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Localização (abaixo de 1 m)**

   Preenchido pelos métodos `trackLocation`.

   * Parâmetros do Target/Dados de contexto do Analytics:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Característica do Audience Management:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nome do ponto de interesse**

   Preenchido pelos métodos trackLocation quando o dispositivo está em um POI definido.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.loc.poi`
   * Característica do Audience Management: `c_a_loc_poi`

* **Distância até o centro do ponto de interesse**

   Preenchido pelos métodos trackLocation quando o dispositivo está em um POI definido.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.loc.dist`
   * Característica do Audience Management: `c_a_loc_dist`

* **Valor de tempo de vida (variável de conversão)**

   Preenchido pelos métodos trackLifetimeValue.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.ltv.amount`
   * Característica do Audience Management: `c_a_ltv_amount`

* **Código de acompanhamento**

   Preenchido pela Aquisição do dispositivo móvel. Gerado automaticamente pelo Adobe Mobile Services.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.referrer.campaign.trackingcode`
   * Característica do Audience Management: `c_a_referrer_campaign_trackingcode`

* **Campaign**

   Nome da campanha, também armazenado na variável da campanha. Preenchido pela Aquisição do dispositivo móvel.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.referrer.campaign.name`
   * Característica do Audience Management: `c_a_referrer_campaign_name`

* **Conteúdo da campanha**

   O nome ou a ID do conteúdo que exibiu o link. Preenchido pela Aquisição do dispositivo móvel.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.referrer.campaign.content`
   * Característica do Audience Management: `c_a_referrer_campaign_content`

* **Meio da campanha**

   Meio de marketing, como banner ou email. Preenchido pela Aquisição do dispositivo móvel.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.referrer.campaign.medium`
   * Característica do Audience Management: `c_a_referrer_campaign_medium`

* **Fonte da campanha**

   Referenciador original, como informativos ou mídias sociais. Preenchido pela Aquisição do dispositivo móvel.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.referrer.campaign.source`
   * Característica do Audience Management: `c_a_referrer_campaign_source`

* **Termo da campanha**

   Palavras-chave pagas ou outros termos que você deseja rastrear com essa aquisição. Preenchido pela Aquisição do dispositivo móvel.

   * Parâmetros do Target/Dados de contexto do Analytics: `a.referrer.campaign.term`
   * Característica do Audience Management: `c_a_referrer_campaign_term`
