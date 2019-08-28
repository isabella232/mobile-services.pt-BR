---
description: Aqui estão as informações de referência para as métricas e dimensões móveis padrão.
keywords: mobile
seo-description: Aqui estão as informações de referência para as métricas e dimensões móveis padrão.
seo-title: Métricas móveis e referências de dimensões
solution: Marketing Cloud, Analytics
title: Métricas móveis e referências de dimensões
topic: Métricas
uuid: 96170 ae 7-8553-4 f 3 e-ae 01-65 e 5 b 664 adf 4
translation-type: tm+mt
source-git-commit: 056bb3edb94c2ceb2961bbe8e4851c20429e1ea2

---


# Mobile metrics and dimensions reference {#mobile-metrics-and-dimensions-reference}

Estas informações ajudam a entender mais sobre as métricas e dimensões móveis padrão.

>[!TIP]
>
>As permissões de dimensão e métrica definidas no Adobe Analytics se aplicam aos Mobile Services. Quando você tenta executar um relatório sem as devidas permissões, ocorre um erro.

## Métricas {#section_6704C815147D44AF96151D626BEB813C}

Esta é a lista de métricas móveis padrão:

* **Primeiras inicializações**

   Acionado na primeira execução após uma instalação ou reinstalação.

* **Atualizações**

   Acionado na primeira execução após uma atualização ou quando o número da versão mudar.

* **Usuários envolvidos diariamente**

   Disparado quando o aplicativo é utilizado em um dia específico.

   >[!TIP]
   >O evento Usuários envolvidos diariamente não é armazenado automaticamente em uma métrica do Analytics. Você deve criar uma regra de processamento que defina um evento personalizado para capturar essa métrica.

* **Usuários envolvidos mensalmente**

   Disparado quando o aplicativo é utilizado durante um mês em

   >[!TIP]
   >O evento Usuários envolvidos mensalmente não é armazenado automaticamente em uma métrica do Analytics. Você deve criar uma regra de processamento que defina um evento personalizado para capturar essa métrica.

* **Inicializações**

   Acionado em uma execução que não seja uma instalação ou atualização. Dispara também quando o aplicativo é trazido para o segundo plano. Por padrão, uma nova inicialização é acionada quando o aplicativo fica em segundo plano por cinco minutos ou mais. The amount of background time before triggering a new launch can be configured in **[!UICONTROL SDK Analytics Options]** on the Manage App Settings page. Para obter mais informações, consulte a linha Tempo limite *da sessão (segundos)* em [Configurar opções do Analytics SDK](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md).

   >[!IMPORTANT]
   >Because how visits in [!UICONTROL Adobe Analytics] and mobile app launches in [!UICONTROL Adobe Mobile Services] are calculated, you might see different results in reporting. Para obter mais informações, consulte [Comparar visitas e inicializações de aplicativos móveis](https://helpx.adobe.com/analytics/kb/compare-visits-and-mobile-app-launches.html).

* **Falhas**

   Acionado quando o aplicativo não fechar (sair) corretamente. Este evento é enviado quando o aplicativo é iniciado após uma falha.

   >[!TIP]
   >O aplicativo é considerado travado se o comando sair não for chamado.

* **Duração total da sessão**

   Duração total agregada da sessão.

## Dimensões {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

Esta é a lista de dimensões móveis padrão:

* **Data de instalação**

   Data da primeira inicialização após a instalação. A data está no formato *MM/DD/AAAA*.

* **ID do aplicativo**

   Armazena o nome e a versão do aplicativo no seguinte formato: `[AppName] [BundleVersion]`. Por exemplo, `myapp 1.1`.

* **Número de Lançamento**

   Número de vezes em que o aplicativo foi iniciado ou trazido para o plano de fundo.

* **Dias desde a primeira utilização**

   Número de dias desde a primeira execução.

* **Dias desde a última utilização**

   Número de dias desde a última utilização.

* **Hora do dia**

   Mede a hora em que o aplicativo foi inicializado e usa o formato numérico de 24 horas. Esta dimensão também é usada para separar o tempo para determinar momentos de pico de utilização.

* **Dias da semana**

   Número do dia da semana no qual o aplicativo foi iniciado.

* **Sistema operacional**

   Sistema operacional do dispositivo.

* **Versão do sistema operacional**

   Versão do sistema operacional.

* **Dias desde a última atualização**

   Número de dias desde que o número de versão do aplicativo foi alterado.

   >[!TIP]
   >
   >Os dias desde a última atualização não são armazenados automaticamente em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

* **Inicializações desde a última atualização**

   Número de inicializações desde que o número de versão do aplicativo foi alterado.

   >[!TIP]
   >
   >As inicializações desde a última atualização não são armazenadas automaticamente em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

* **Nome do dispositivo**

   Armazena o nome do dispositivo. No iOS, uma sequência de dois dígitos separados por vírgulas identifica o dispositivo iOS. O primeiro número representa a geração do dispositivo e o segundo número de membros da família do dispositivo. Para obter uma lista de nomes comuns, consulte [Versões do dispositivo iOS](/help/ios/reference/device-versions.md).

* **Nome da operadora**

   Armazena o nome do provedor de serviço móvel.

* **Resolução**

   Largura e altura em pixels reais.
