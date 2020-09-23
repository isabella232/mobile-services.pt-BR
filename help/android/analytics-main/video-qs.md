---
description: Estas são algumas informações sobre a avaliação de vídeo no Android vindas da solução de avaliação de vídeo.
keywords: android;library;mobile;sdk
seo-description: Estas são algumas informações sobre a avaliação de vídeo no Android vindas da solução de avaliação de vídeo.
seo-title: Análise de vídeo
solution: Experience Cloud,Analytics
title: Análise de vídeo
topic: Developer and implementation
uuid: a137cc27-dc28-48c0-b08e-2ca17d2c7e1d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 85%

---


# Análise de vídeo {#video-analytics}

Estas são algumas informações sobre a avaliação de vídeo no Android vindas da solução de avaliação de vídeo.

>[!TIP]
>
>Durante a reprodução do vídeo, chamadas &quot;heartbeat&quot; frequentes são enviadas a esse serviço para medir o tempo reproduzido. Essas chamadas de heartbeat são enviadas a cada 10 segundos, o que resulta em métricas granulares de envolvimento com o vídeo e relatórios de repercussão de vídeo mais precisos. Para obter mais informações sobre a solução de medição de vídeos da Adobe, consulte [Medição de áudio e vídeo no Adobe Analytics](https://docs.adobe.com/content/help/pt-BR/media-analytics/using/media-overview.html).

O processo geral para medição de vídeo é parecido em todas as plataformas. Este conteúdo oferece uma visão geral das tarefas do desenvolvedor com amostras de código. A tabela a seguir lista os dados de mídia que são enviados para o Analytics. As regras de processamento são usadas para mapear os dados de contexto para uma variável do Analytics.

## Mapear eventos do player para variáveis do Analytics {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

* **a.media.name**
   * Tipo de variável: eVar
      * Expiração padrão: visita
      * Custom Insight (s.prop, usado para definição de caminho de vídeo)
   * (**Obrigatório**) Quando um visitante visualização o vídeo de alguma forma, essa variável de dados de contexto coleta o nome do vídeo, conforme especificado na implementação. É possível adicionar classificações para essa variável.
   * (**Optional**) The Custom Insight variable provides video pathing information.

* **a.media.name**
   * Tipo de variável: Insight personalizado (s.prop)
   * (**Opcional**) Fornece informações sobre o caminho do vídeo.

      >[!IMPORTANT]
      >
      >O caminho deve ser habilitado para esta variável pelo ExpCare.
   * Tipo de evento: Insight personalizado (s.prop)

* **a.media.segment**
   * Tipo de variável: eVar
   * Expiração padrão: visualização de página
   * (**Required**) Collects video segment data, including the segment name and the order in which the segment occurs in the video.

      Essa variável é preenchida com a habilitação da variável `segmentByMilestones` durante o rastreamento automático de eventos de player, ou ao configurar um nome de segmento personalizado durante o rastreamento manual dos eventos do player. Por exemplo, quando um visitante exibe o primeiro segmento em um vídeo, o SiteCatalyst pode coletar as seguintes informações no eVar Segmentos: `1:M:0-25`.

      O método padrão de coleta de dados de vídeo coleta dados nos seguintes pontos:

      * início do vídeo (reproduzir)
      * início do segmento
      * fim do vídeo (parar)

      O Analytics conta a primeira visualização de segmento no início do segmento, quando o visitante começa a assistir. As visualizações de segmento subsequentes ocorrem conforme o segmento começa.


* **a.contentType**
   * Tipo de variável: eVar
   * Expiração padrão: visualização de página
   * Coleta dados sobre o tipo de conteúdo que é visualizado por um visitante.

      Ocorrências enviadas por meio da medição de vídeo recebem um tipo de conteúdo de `video`. Da perspectiva de avaliação do vídeo, o **Tipo de conteúdo** permite que você identifique visitantes de vídeo e, portanto, calcule as taxas de conversão do vídeo.

* **a.media.timePlayed**
   * Tipo de variável: evento
   * Tipo: contador
   * Conta o tempo, em segundos, que é gasto assistindo a um vídeo desde o último processo de coleta de dados (solicitação de imagem).

* **a.media.view**
   * Tipo de variável: evento
   * Tipo: contador
   * Indica que um visitante visualizou uma parte de um de vídeo.

      No entanto, não fornece informações sobre quanto ou a qual parte de um segmento de vídeo o visitante assistiu.

* **a.media.segmentView**
   * Tipo de variável: evento
   * Tipo: contador
   * Indica que um visitante visualizou uma parte de um segmento de vídeo.

      No entanto, não fornece informações sobre quanto ou a qual parte de um segmento de vídeo o visitante assistiu.

* **a .media.complete**
   * Tipo de variável: evento
   * Tipo: contador
   * Indica se o usuário exibiu um vídeo completo.

      Por padrão, o evento completo é avaliado um segundo antes do fim do vídeo. Durante a implementação, você pode especificar quantos segundos a partir do fim do vídeo você gostaria de considerar uma visualização como concluída. Para vídeos ao vivo e outros fluxos que não tenham um fim definido, você pode especificar um ponto personalizado para avaliar conclusões (por exemplo, após um tempo específico de exibição).


## Definir as configurações de mídia {#section_929945D4183C428AAF3B983EFD3E2500}

Defina um objeto `MediaSettings` com as configurações que deseja usar para monitorar o vídeo:

```java
MediaSettings mySettings = Media.settingsWith("name", 10, "playerName", "playerId");
```

## Rastrear eventos de vídeo {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Para medir a reprodução de vídeo, os métodos `mediaPlay`, `mediaStop` e `mediaClose` devem ser chamados nos momentos apropriados. Por exemplo, quando o reprodutor é pausado, chame `mediaStop`. `mediaPlay` é chamado quando a reprodução começa ou é retomada.

## Classes {#section_16838332727348F990305C0C6B0D795C}

**Classe: MediaSettings**

```java
public String name; 
public String playerName; 
public String playerID; 
public double length; 
public String channel; 
public String milestones; 
public String offsetMilestones; 
public boolean segmentByMilestones; 
public boolean segmentByOffsetMilestones; 
public int trackSeconds = 0; 
public int completeCloseOffsetThreshold = 1; 
 
// MediaAnalytics Ad settings 
public String parentName; 
public String parentPod; 
public String CPM; 
public double parentPodPosition; 
public boolean isMediaAd;
```

**Classe: MediaState**

```java
public Date openTime = new Date(); 
public String name; 
public String segment; 
public String playerName; 
public String mediaEvent; 
public int offsetMilestone; 
public int segmentNum; 
public int milestone; 
public double length; 
public double offset; 
public double percent; 
public double timePlayed; 
public double segmentLength; 
public boolean complete = false; 
public boolean clicked = false; 
public boolean ad; 
public boolean eventFirstTime;
```

## Classe de medição de mídia e referência de método {#section_50DF9359A7B14DF092634C8E913C77FE}

Estes são os métodos na classe de medição de mídia:

* **settingsWith**

   Retorna um objeto `MediaSettings` com parâmetros especificados.

   * Esta é a sintaxe para este método:

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

   * Esta é a amostra de código para este método:

      ```java
      MediaSettingsmySettings = Media.settingsWith("name", 10, "playerName", "playerId");
      ```

* **adSettingsWith**

   Retorna um objeto `MediaSettings` para utilizar no monitoramento de um vídeo de anúncio.
   * Esta é a sintaxe para este método:

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

* **open**

   Abre um objeto `MediaSettings` para monitoramento.

   * Esta é a sintaxe para este método:

      ```java
      public static void open(MediaSettings settings, MediaCallback callback); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.open(mySettings, new Media.MediaCallback() { 
        @Override 
        public void call(Object item)
        {//  monitor  callback  if  you  want  to  be  notified  every  second  the  media  is  playing  }
        }); 
      ```

   * **close**

      Fecha o item de mídia com *nome*.

      * Esta é a sintaxe para este método:

      ```java
      public static void close(String name);
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.close("name"); 
      ```


* **play**
   * Reproduz o item de mídia com o nome *name* no *offset* em questão em segundos.
   * Esta é a sintaxe para este método:

      ```java
      publicstatic void play(String name, double offset); 
      ```

* **concluído**

   Marca manualmente o item de mídia como concluído no *offset* em questão em segundos.

   * Esta é a sintaxe para este método:

      ```java
      public static void complete(String name, double offset); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.complete("name", 0); 
      ```

* **stop**

   Notifica ao módulo de mídia que o vídeo foi interrompido ou pausado no *offset* em questão.

   * Esta é a sintaxe para este método:

      ```java
      public static void stop(String name, double offset); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.stop("name", 0);
      ```

* **click**

   Notifica ao módulo de mídia que o item de mídia foi clicado.

   * Esta é a sintaxe para este método:

      ```java
      public static void click(String name double offset); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.click("name", 0);
      ```

* **track**

   Envia uma chamada de ação de rastreamento (sem exibição de página) para o estado de mídia atual.

   * Esta é a sintaxe para este método:

      ```java
      publicstatic void track(String name, Map<String, Object> data); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      Media.track("name", null); 
      ```
