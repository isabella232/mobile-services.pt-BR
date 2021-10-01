---
description: O processo geral para medição de vídeo é muito parecido em todas as plataformas AppMeasurement. Esta seção fornece uma visão geral básica das tarefas do desenvolvedor junto com exemplos de código.
title: Análise de vídeo
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
exl-id: 90da1a9e-2faa-429c-969e-869ebedf08cc
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 68%

---

# Análise de vídeo {#video-analytics}

O processo geral para medição de vídeo é muito parecido em todas as plataformas AppMeasurement. Esta seção fornece uma visão geral básica das tarefas do desenvolvedor junto com exemplos de código.

Para obter mais informações sobre a Medição de vídeo, consulte o guia [Medição de mídia de transmissão no Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=pt-BR) .  A tabela a seguir lista os dados de mídia que são enviados para o Analytics. Use as regras de processamento para mapear os dados de contexto na coluna Variável de dados de contexto para uma variável do Analytics, conforme descrito na coluna Tipo de variável .

## Mapear eventos do player para variáveis do Analytics

* **a.media.name**

   (Obrigatório) Coleta o nome do vídeo, conforme especificado na implementação, quando um visitante visualiza o vídeo de alguma forma. É possível adicionar classificações para essa variável.

   **(Opcional)** A variável Custom Insight fornece informações de definição de caminho de vídeo.

   * Nome da variável: eVar
      * Expiração padrão: visita
      * Custom Insight (s.prop, usado para definição de caminho de vídeo)

* **a.media.name**

   (**Opcional**) Fornece informações sobre o caminho do vídeo. O caminho deve ser habilitado para esta variável pelo Atendimento ao cliente.

   * Tipo de evento: Insight personalizado (s.prop)
   * Custom Insight (s.prop)

* **a.media.segment**

   (**Obrigatório**) Coleta dados de segmento do vídeo, incluindo o nome do segmento e a ordem na qual ele ocorre no vídeo. Essa variável é preenchida com a habilitação da variável `segmentByMilestones` durante o monitoramento de eventos de player de modo automático, ou ao configurar um nome de segmento personalizado durante o monitoramento manual dos eventos do player.

   Por exemplo, quando um visitante exibe o primeiro segmento em um vídeo, o SiteCatalyst pode coletar `1:M:0-25` no eVar Segmentos. O método padrão de coleta de dados de vídeo coleta dados no início do vídeo (reproduzir), início do segmento e fim do vídeo (parar).

   O Analytics conta a primeira visualização de segmento no início do segmento, quando o visitante começa a assistir. As visualizações de segmento subsequentes ocorrem conforme o segmento começa.

   * Tipo de variável: eVar
   * Expiração padrão: visualização de página

* **a.contentType**

   Coleta dados sobre o tipo de conteúdo exibido por um visitante. Ocorrências enviadas por avaliação de vídeo recebem um tipo de conteúdo de &quot;vídeo&quot;. Essa variável não precisa ser reservada exclusivamente para rastreamento de vídeo. Quando outros conteúdos relatam o tipo por meio da mesma variável, é possível analisar a distribuição de visitantes em tipos diferentes de conteúdo. Por exemplo, é possível marcar outros tipos de conteúdo por meio de valores como &quot;artigo&quot; ou &quot;página do produto&quot; com essa variável. Da perspectiva de avaliação do vídeo, o Tipo de conteúdo permite que você identifique visitantes de vídeo e, portanto, calcule as taxas de conversão do vídeo.

   * Tipo de variável: eVar
   * Expiração padrão: visualização de página

* **a.media.timePlayed**

   Contabiliza o tempo, em segundos, que é gasto com a exibição de um vídeo desde o último processo de coleta de dados (solicitação da imagem).

   * Tipo de variável: Evento
   * Tipo: contador

* **a.media.view**

   Indica que um visitante visualizou uma parte de um de vídeo. No entanto, não fornece informações sobre quanto ou qual parte de um vídeo o visitante visualizou.

   * Tipo de variável: Evento
   * Tipo: contador

* **a.media.segmentView**

   Indica que um visitante visualizou uma parte de um segmento de vídeo. No entanto, não fornece informações sobre quanto ou qual parte de um vídeo o visitante visualizou.

   * Tipo de variável: Evento
   * Tipo: contador

* **a .media.complete**

   Indica se o usuário exibiu um vídeo completo. Por padrão, o evento completo é avaliado um segundo antes do fim do vídeo. Durante a implementação, é possível especificar quantos segundos a partir do fim do vídeo são necessários para considerar a visualização como concluída. Para vídeos ao vivo e outras transmissões que não têm um fim definido, você pode especificar um ponto personalizado para medir as conclusões. Por exemplo, depois de um tempo de exibição específico.

   * Tipo de variável: Evento
   * Tipo: contador

## Rastrear eventos de vídeo {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Para avaliar a reprodução de vídeo, os métodos `mediaPlay`, `mediaStop`, e `mediaClose` devem ser chamados em momentos apropriados. Por exemplo, quando o reprodutor está pausado, `mediaStop`. `mediaPlay` é chamado quando a reprodução começa ou é retomada.

## Referência de método e classe de medição de mídia {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   Abre um vídeo para rastreamento.

   * Esta é a sintaxe para este método:

      ```cpp
      void open(QString name, double length, QString playerName, QString playerID = QString()); 
      ```

   * Esta é a amostra de código para este método:

      ```cpp
        ADBMediaAnalytics::sharedInstance()->open("name", 10.0, "playerName", "playerID"); 
      ```

* **openAd**

   Abre um objeto `MediaSettings` para monitoramento.

   * Esta é a sintaxe para este método:

      ```cpp
      void openAd(QString name, double length, QString playerName, QString parentName, QString parentPod, double parentPodPosition, QString CPM); 
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->openAd("name", 10, "playerName", "parentName", "podName", 0, "CPM"); 
      ```

* **close**

   Fecha o item de mídia com o nome *`name`*.

   * Esta é a sintaxe para este método:

      ```cpp
      void close(QString name);
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   Reproduz o item de mídia chamado *`name`* no *`offset`* especificado (em segundos).

   * Esta é a sintaxe para este método:

      ```cpp
      void play(QString name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **concluído**

   Marca manualmente o item de mídia como concluído no *`offset`* em questão (em segundos).

   * Esta é a sintaxe para este método:

      ```cpp
      void complete(QString name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->complete("name", 0);
      ```

* **stop**

   Notifica ao módulo de mídia que o vídeo foi interrompido ou pausado no *offset* em questão.

   * Esta é a sintaxe para este método:

      ```cpp
      stop(QString name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->stop("name", 0);
      ```

* **click**

   Notifica ao módulo de mídia que o item de mídia foi clicado.

   * Esta é a sintaxe para este método:

      ```cpp
      void click(QString name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name", 0);
      ```

* **track**

   Envia uma chamada de ação de rastreamento (sem exibição de página) para o estado de mídia atual.

   * Esta é a sintaxe para este método:

      ```cpp
      track(QString name, QHash<QString, QString> additionalData = QHash<QString, QString>()); 
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->track("name", null);
      ```
