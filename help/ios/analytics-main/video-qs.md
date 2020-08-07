---
description: Estas são algumas informações sobre a medição de vídeos no iOS usando a medição de vídeos por etapas.
seo-description: Estas são algumas informações sobre a medição de vídeos no iOS usando a medição de vídeos por etapas.
seo-title: Análise de vídeo
solution: Marketing Cloud,Analytics
title: Análise de vídeo
topic: Developer and implementation
uuid: d75fa415-78f6-4f50-a563-76949f040138
translation-type: tm+mt
source-git-commit: c64e2fa7cee3cd35c4574e5007406b7604c99499
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 81%

---


# Análise de vídeo {#video-analytics}

Estas são algumas informações sobre a medição de vídeos no iOS usando a medição de vídeos por etapas.

>[!TIP]
>
>Durante a reprodução do vídeo, chamadas &quot;heartbeat&quot; frequentes são enviadas a esse serviço para medir o tempo reproduzido. Essas chamadas de heartbeat são enviadas a cada 10 segundos, o que resulta em métricas granulares de envolvimento com o vídeo e relatórios de repercussão de vídeo mais precisos. Para obter mais informações, consulte [Medição de áudio e vídeo no Adobe Analytics](https://docs.adobe.com/content/help/pt-BR/media-analytics/using/media-overview.html).

O processo geral para avaliar vídeos é muito semelhante em todas as plataformas. Este conteúdo fornece uma visão geral básica das tarefas do desenvolvedor com exemplos de código.

## Mapear eventos do player para variáveis do Analytics {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

A tabela a seguir lista os dados de mídia que são enviados para o Analytics. Usar as regras de processamento para mapear os dados de contexto para uma variável do Analytics.

* **a.media.name**

   (Obrigatório) Coleta o nome do vídeo, conforme especificado na implementação, quando um visitante exibe o vídeo. É possível adicionar classificações para essa variável.

   (Opcional) A variável Custom Insight fornece informações de definição de caminho de vídeo.

   * Tipo de variável: eVar
   * Expiração padrão: visita
   * Custom Insight (s.prop, usado para definição de caminho de vídeo)

* **a.media.name**

   (Opcional) Fornece informações sobre o caminho do vídeo. A definição de caminho deve ser ativada para essa variável pelo Atendimento ao cliente.

   * Tipo de variável: Insight personalizado (s.prop)
   * Tipo de evento: Insight personalizado (s.prop)

* **a.media.segment**

   (Obrigatório) Coleta dados de segmento do vídeo, incluindo o nome do segmento e a ordem na qual ele ocorre no vídeo. Essa variável é preenchida com a habilitação da variável `segmentByMilestones` durante o monitoramento de eventos de player de modo automático, ou ao configurar um nome de segmento personalizado durante o monitoramento manual dos eventos do player. Por exemplo, quando um visitante exibe o primeiro segmento em um vídeo, o SiteCatalyst pode coletar as seguintes informações no eVar de segmentos `1:M:0-25`.

   O método padrão de coleta de dados de vídeo coleta dados nos seguintes pontos:

   * start de vídeo (play)
   * início do segmento
   * fim do vídeo (parar)

   O Analytics conta a primeira visualização de segmento no start do segmento, quando o visitante start assistindo. O segmento subsequente visualização quando o segmento começa.

   * Tipo de variável: eVar
   * Expiração padrão: visualização de página


* **a.contentType**

   Coleta dados sobre o tipo de conteúdo que é visualizado por um visitante. Hits sent by video measurement are assigned a content type of `video`. This variable does not need to be reserved exclusively for video tracking. Quando outros conteúdos relatam tipos usando essa mesma variável, você pode analisar a distribuição de visitantes entre os diferentes tipos de conteúdo. Por exemplo, é possível marcar outros tipos de conteúdo por meio de valores como “artigo” ou “página do produto” com essa variável. Da perspectiva da avaliação de vídeo, o Tipo de conteúdo permite identificar os visitantes e calcular as taxas de conversão do vídeo.

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

* **a.media.complete**

   Indica se o usuário exibiu um vídeo completo. Por padrão, o evento completo é avaliado um segundo antes do fim do vídeo. Durante a implementação, é possível especificar quantos segundos a partir do fim do vídeo são necessários para considerar a visualização como concluída. Para vídeos ao vivo e outros fluxos que não tenham um fim definido, você pode especificar um ponto personalizado para avaliar conclusões, por exemplo, após um tempo de exibição específico.

   * Tipo de variável: Evento
   * Tipo: contador

## Definir as configurações de mídia {#section_929945D4183C428AAF3B983EFD3E2500}

Configure um objeto `ADBMediaSettings` com as configurações que deseja usar para rastrear vídeos:

```objective-c
ADBMediaSettings *mediaSettings = [ADBMobile mediaCreateSettingsWithName:MEDIA_NAME  
length:MEDIA_LENGTH playerName:PLAYER_NAME playerID:PLAYER_ID]; 
 
// milestone tracking. Use either standard milestones (percentage of total length) 
// or offset milestones (seconds elapsed from the beginning of the video) 
mediaSettings.milestones = @"25,50,75"; 
mediaSettings.segmentByMilestones = YES; 
 
mediaSettings.offsetMilestones = @"60,120"; 
mediaSettings.segmentByOffsetMilestones = YES; 
 
// seconds tracking - sends a hit every x seconds 
mediaSettings.trackSeconds = 30; // sends a hit every 30 seconds 
 
// open the video 
[ADBMobile mediaOpenWithSettings:mediaSettings callback:nil]; 
 
// You are now ready to play the video, for example, [movieViewController.moviePlayer play]; 
// Note the mediaPlay, mediaStop and mediaClose methods are called in the 
// event handlers described in the next section
```

## Rastrear eventos de vídeo {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Para avaliar a reprodução de vídeo, os métodos `mediaPlay`, `mediaStop`, e `mediaClose` devem ser chamados em momentos apropriados. Por exemplo, quando o reprodutor está pausado, `mediaStop`. `mediaPlay` é chamado quando a reprodução começa ou é retomada.

O seguinte exemplo demonstra como configurar as notificações e chamar os métodos de mídia para avaliar o vídeo:

```objective-c
// configure notifications for when the video is finished, and when the 
media playback state changes 
 
- (void) configureNotifications:(MPMoviePlayerController *) movieController { 
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaFinishedCallback:) 
  name: MPMoviePlayerPlaybackDidFinishNotification 
  object: movieController]; 
  
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaPlaybackChangedCallback:) 
  name: MPMoviePlayerPlaybackStateDidChangeNotification 
  object: movieController]; 
} 
 
// define your notification callbacks. 
 
- (void) mediaFinishedCallback: (NSNotification*) notification { [ADBMobile mediaClose:MEDIA_NAME];} 
 
- (void) mediaPlaybackChangedCallback: (NSNotification*) notification { 
 MPMoviePlayerController *mediaController = notification.object; 
 if (mediaController.playbackState == MPMoviePlaybackStatePlaying) { 
  [ADBMobile mediaPlay:MEDIA_NAME offset: isnan(mediaController.currentPlaybackTime) ? 0.0 : mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingBackward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingForward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStatePaused) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateInterrupted) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateStopped) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
}
```

## Classes {#section_16838332727348F990305C0C6B0D795C}

### Classe: ADBMediaSettings

```objective-c
bool segmentByMilestones; 
bool segmentByOffsetMilestones; 
double length; 
NSString *channel; 
NSString *name; 
NSString *playerName; 
NSString *playerID; 
NSString *milestones; 
NSString *offsetMilestones; 
NSUInteger trackSeconds; 
NSUInteger completeCloseOffsetThreshold; 
// settings used for ad tracking. For  
bool isMediaAd; 
double parentPodPosition; 
NSString *CPM; 
NSString *parentName; 
NSString *parentPod; 
```

### Classe: ADBMediaState

```objective-c
bool ad; 
bool clicked; 
bool complete; 
bool eventFirstTime; 
double length; 
double offset; 
double percent; 
double segmentLength; 
double timePlayed; 
double timePlayedSinceTrack; 
double timestamp; 
NSDate *openTime  
NSString *name 
NSString *playerName 
NSString *mediaEvent 
NSString *segment 
NSUInteger milestone 
NSUInteger offsetMilestone 
NSUInteger segmentNum 
NSUInteger eventType
```

## Referência de método e classe de medição de mídia {#section_50DF9359A7B14DF092634C8E913C77FE}

* **mediaCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;playerID:**

   Retorna um objeto `ADBMediaSettings` com parâmetros especificados.

   * Esta é a sintaxe para este método:

      ```objective-c
      +(ADBMediaSettings *) mediaCreateSettingsWithName:(NSString *)name
                                                 length:(double)length
                                              playerName:(NSString *)playerName
                                               playerID:(NSString *)playerID;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      ADBMediaSettings *myCatSettings =
            [ADBMobile mediaCreateSettingsWithName:@"catVideo"                                               length:85
                                        playerName:@"catVideoPlayer"
                                          playerID:@"catPlayerId"]; 
      ```

* **mediaAdCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;parentName:&#x200B;parentPod:&#x200B;parentPodPosition:&#x200B;CPM:**

   Retorna um objeto `ADBMediaSettings` a ser utilizado no rastreamento de um vídeo de anúncio.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (ADBMediaSettings *) mediaAdCreateSettingsWithName:(NSString *)name
                                                    length:(double)length   
                                                playerName:(NSString *)playerName
                                                parentName:(NSString *)parentName
                                                 parentPod:(NSString *)parentPod
                                        parentPodPosition:(double)parentPodPosition
                                                      CPM:(NSString *)CPM; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
        ADBMediaSettings *mySettings = 
             [ADBMobile mediaAdCreateSettingsWithName:@"ad"                                       length:30
                                           playerName:@"adPlayer"
                                           parentName:@"catVideo"
                                           parentPod:@"catCollection"
                                           parentPodPosition:2
                                                        CPM:nil];
      ```

* **mediaOpenWithSettings:&#x200B;callback:**

   Abre um objeto `ADBMediaSettings` para rastreamento.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) mediaOpenWithSettings:(ADBMediaSettings *)settings
                            callback:(void (^)(ADBMediaState *mediaState))callback; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile mediaOpenWithSettings:mySettings callback:^(ADBMediaState *mediaState) {
           // do something with media state if you want}];
      ```

* **mediaClose:**

   Fecha o item de mídia com *nome*.

   * Esta é a sintaxe para este método:

      ```objective-c
       + (void) mediaClose:(NSString *)name; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile mediaClose:@"kittiesPlaying"];
      ```

* **mediaPlay:&#x200B;offset:**

   Reproduz o item de mídia com o nome *nome* no *deslocamento* em questão (em segundos).

   * Esta é a sintaxe para este método:

      ```objective-c
       + (void) mediaPlay:(NSString *)name offset:(double)offset;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile mediaPlay:@"cats" offset:25];
      ```

* **mediaComplete:&#x200B;offset:**

   Marca manualmente o item de mídia como concluído no *offset* em questão (em segundos).

   * Esta é a sintaxe para este método:

      ```objective-c
       + (void) mediaComplete:(NSString *)name offset:(double)offset;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
       [ADBMobile mediaComplete:@"meowzah" offset:90]; 
      ```

* **mediaStop:&#x200B;offset:**

   Notifica ao módulo de mídia que o vídeo foi interrompido ou pausado no *offset* em questão.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) mediaStop:(NSString *)name offset:(double)offset; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile mediaStop:@"toonses" offset:30]; 
      ```

* **mediaClick:&#x200B;offset:**

   Notifica ao módulo de mídia que o item de mídia foi clicado.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) mediaClick:(NSString *)name offset:(double)offset;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile mediaClick:@"soManyCats" offset:47];
      ```

* **mediaTrack:&#x200B;withData:**

   Envia uma chamada de ação de rastreamento (sem exibição de página) para o estado de mídia atual.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) mediaTrack:(NSString *)name withData:(NSDictionary *)data;
      ```

