---
description: O processo geral para medição de vídeo é muito parecido em todas as plataformas AppMeasurement. Esta seção fornece uma visão geral básica das tarefas do desenvolvedor junto com exemplos de código.
seo-description: O processo geral para medição de vídeo é muito parecido em todas as plataformas AppMeasurement. Esta seção fornece uma visão geral básica das tarefas do desenvolvedor junto com exemplos de código.
seo-title: Análise de vídeo
title: Análise de vídeo
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# Análise de vídeo {#video-analytics}

O processo geral para medição de vídeo é muito parecido em todas as plataformas AppMeasurement. Esta seção fornece uma visão geral básica das tarefas do desenvolvedor junto com exemplos de código.

Para obter mais informações sobre a avaliação de vídeo, consulte [Medição de áudio e vídeo no guia do Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html) .  A tabela a seguir lista os dados de mídia que são enviados para o Analytics. Use as regras de processamento para mapear os dados de contexto na coluna Variável de dados de contexto a uma variável do Analytics, conforme descrito na coluna Tipo de variável.

## Map player events to Analytics variables

* **a.media.name**

   (Obrigatório) Coleta o nome do vídeo, conforme especificado na implementação, quando um visitante visualiza o vídeo de alguma forma. É possível adicionar classificações para esta variável.

   **(Opcional)** A variável Insight personalizado fornece informações de definição de caminho de vídeo.

   * Nome da variável: eVar
      * Expiração padrão: visita
      * Insight personalizado (s.prop, usado para caminhos de vídeo)

* **a.media.name**

   (**Opcional**) Fornece informações sobre o caminho do vídeo. Os caminhos devem ser habilitados para esta variável pelo ClientCare.

   * Tipo de evento: Insight personalizado (s.prop)
   * Insight personalizado (s.prop)

* **a.media.segment**

   (**Obrigatório**) Coleta dados de segmento do vídeo, incluindo o nome do segmento e a ordem na qual ele ocorre no vídeo. Essa variável é preenchida com a habilitação da variável `segmentByMilestones` durante o monitoramento de eventos de player de modo automático, ou ao configurar um nome de segmento personalizado durante o monitoramento manual dos eventos do player.

   For example, when a visitor views the first segment in a video, SiteCatalyst might collect `1:M:0-25` in the Segments eVar. The default video data collection method collects data at the video start (play), segment begin, and video end (stop) points.

   O sistema conta a primeira exibição de segmento no início, quando o visitante começa a assistir. As exibições de segmento subsequente ocorrem quando o segmento começa.

   * Tipo de variável: eVar
   * Expiração padrão: visualização de página

* **a.contentType**

   Coleta dados sobre o tipo de conteúdo exibido por um visitante. Ocorrências enviadas por meio da avaliação de vídeo recebem um tipo de conteúdo chamado “vídeo”. Essa variável não precisa estar reservada exclusivamente para o rastreamento de vídeo. Quando outros conteúdos relatam o tipo por meio da mesma variável, é possível analisar a distribuição de visitantes em tipos diferentes de conteúdo. Por exemplo, é possível marcar outros tipos de conteúdo por meio de valores como “artigo” ou “página do produto” com essa variável. Da perspectiva de avaliação do vídeo, o tipo de conteúdo permite que você identifique visitantes de vídeo e, portanto, calcule as taxas de conversão do vídeo.

   * Tipo de variável: eVar
   * Expiração padrão: visualização de página

* **a.media.timePlayed**

   Contabiliza o tempo, em segundos, que é gasto com a exibição de um vídeo desde o último processo de coleta de dados (solicitação da imagem).

   * Tipo de variável: Evento
   * Tipo: contador

* **a.media.view**

   Indica que um visitante visualizou uma parte de um vídeo. No entanto, não fornece informações algumas sobre quanto ou a que parte de um vídeo o visitante assistiu.

   * Tipo de variável: Evento
   * Tipo: contador

* **a.media.segmentView**

   Indica que um visitante visualizou uma parte de um segmento de vídeo. No entanto, não fornece informações algumas sobre quanto ou a que parte de um vídeo o visitante assistiu.

   * Tipo de variável: Evento
   * Tipo: contador

* **a .media.complete**

   Indica se o usuário exibiu um vídeo completo. Por padrão, o evento completo é avaliado um segundo antes do fim do vídeo. Durante a implementação, é possível especificar quantos segundos a partir do fim do vídeo são necessários para considerar a visualização como concluída. Para o vídeo ao vivo e outros fluxos sem um fim definido, é possível especificar um ponto personalizado para avaliar conclusões. Por exemplo, após um tempo de exibição específico.

   * Tipo de variável: Evento
   * Tipo: contador

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. Por exemplo, quando o reprodutor está pausado, `mediaStop`. `mediaPlay` é chamado quando a reprodução começa ou é retomada.

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

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

   Closes the media item named *`name`*.

   * Esta é a sintaxe para este método:

      ```cpp
      void close(QString name);
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   Plays the media item named *`name`* at the given *`offset`* (in seconds).

   * Esta é a sintaxe para este método:

      ```cpp
      void play(QString name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **conclúido**

   Marca manualmente o item de mídia como concluído no *`offset`em questão (em segundos).*

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
