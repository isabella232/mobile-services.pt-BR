---
description: Aqui estão as informações de referência para as métricas e dimensões móveis padrão.
keywords: dispositivos móveis
solution: Experience Cloud,Analytics
title: Métricas móveis e referências de dimensões
topic-fix: Metrics
uuid: 96170ae7-8553-4f3e-ae01-65e5b664adf4
exl-id: ddfbf11e-a4c3-4d59-92b3-1d192dc3e7cd
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 100%

---

# Referência de métricas e dimensões móveis {#mobile-metrics-and-dimensions-reference}

Essas informações ajudam você a entender mais sobre as métricas e dimensões móveis por padrão.

>[!TIP]
>
>As permissões de dimensão e métrica definidas no Adobe Analytics se aplicam ao Mobile Services. Quando você tenta executar um relatório sem as permissões apropriadas, ocorre um erro.

## Métricas {#section_6704C815147D44AF96151D626BEB813C}

Esta é a lista de métricas móveis por padrão:

* **Primeiras inicializações**

   Acionado na primeira execução após uma instalação ou reinstalação.

* **Atualizações**

   Acionado na primeira execução após uma atualização ou quando o número da versão mudar.

* **Usuários envolvidos diariamente**

   Disparado quando o aplicativo é utilizado em um dia específico.

   >[!TIP]
   >
   >O evento Usuários envolvidos diariamente não é armazenado automaticamente em uma métrica do Analytics. Você deve criar uma regra de processamento que defina um evento personalizado para capturar essa métrica.

* **Usuários envolvidos mensalmente**

   Disparado quando o aplicativo é utilizado durante um mês em

   >[!TIP]
   >O evento Usuários envolvidos mensalmente não é armazenado automaticamente em uma métrica do Analytics. Você deve criar uma regra de processamento que defina um evento personalizado para capturar essa métrica.

* **Inicializações**

   Acionado em uma execução que não seja uma instalação ou atualização. Dispara também quando o aplicativo é trazido para o segundo plano. Por padrão, uma nova inicialização é acionada quando o aplicativo fica em segundo plano por cinco minutos ou mais. É possível configurar a quantidade de tempo em segundo plano antes de uma nova inicialização ser acionada nas **[!UICONTROL Opções de SDK do Analytics]**, na página Gerenciar configurações do aplicativo. Para obter mais informações, consulte o *Limite da sessão (segundos)* em [Configurar opções do SDK Analytics](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md).

   >[!IMPORTANT]
   >Devido à forma como as visitas e inicializações de aplicativos móveis são calculadas no [!UICONTROL Adobe Analytics] e no [!UICONTROL Adobe Mobile Services], você poderá ver diferentes resultados nos relatórios. Para obter mais informações, consulte [Comparar visitas e inicializações de aplicativos móveis](https://helpx.adobe.com/br/analytics/kb/compare-visits-and-mobile-app-launches.html).

* **Falhas**

   Acionado quando o aplicativo não sai corretamente. Esse evento é enviado quando o aplicativo é iniciado após uma falha.

   >[!TIP]
   >O aplicativo pode falhar se o comando Sair não for invocado.

* **Duração total da sessão**

   Duração total agregada da sessão.

## Dimensões {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

Esta é a lista de dimensões móveis por padrão:

* **Data de instalação**

   Data do primeiro lançamento após a instalação. A data está no formato *MM/DD/AAAA*.

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
   >Os Dias desde a última atualização não são armazenados automaticamente em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

* **Inicializações desde a última atualização**

   Número de inicializações desde que o número de versão do aplicativo foi alterado.

   >[!TIP]
   >
   >As Inicializações desde a última atualização não são armazenadas automaticamente em uma variável do Analytics. Para usá-lo em relatórios, será necessário criar uma regra de processamento para copiar esse valor para uma variável Analytics.

* **Nome do dispositivo**

   Armazena o nome do dispositivo. No iOS, uma sequência de dois dígitos separada por vírgulas identifica o dispositivo iOS. O primeiro número representa a geração do dispositivo e o segundo representa versões dos diferentes membros da família do dispositivo. Para obter uma lista de nomes comuns, consulte [Versões do dispositivo iOS](/help/ios/reference/device-versions.md).

* **Nome da operadora**

   Armazena o nome do provedor de serviço móvel.

* **Resolução**

   Largura e altura em pixels reais.
