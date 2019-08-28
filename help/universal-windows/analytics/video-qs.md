---
description: Informações para ajudá-lo com a Análise de vídeo.
seo-description: Informações para ajudá-lo com a Análise de vídeo.
seo-title: Análise de vídeo
solution: Marketing Cloud, Analytics
title: Análise de vídeo
topic: Desenvolvedor e implementação
uuid: f 45 dac 3 b-cd 2 e -4 fba-a 3 b 2-c 243640 ecfa 4
translation-type: tm+mt
source-git-commit: 1c0b7dadc28f772e903baa8605016e70f05081d7

---


# Análise de vídeo {#video-analytics}

Informações para ajudá-lo com a Análise de vídeo.

Video measurement is described in detail in the [Measuring video and audio in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html) guide. O processo geral para medição de vídeo é muito parecido em todas as plataformas AppMeasurement. Esta seção de início rápido fornece uma visão geral básica das tarefas do desenvolvedor junto com exemplos de código.

A tabela a seguir lista os dados de mídia que são enviados para o Analytics. Use as regras de processamento para mapear os dados de contexto para uma variável do Analytics.

* **a.media.name**

   **(Obrigatório**) Coleta o nome do vídeo, conforme especificado na implementação, quando um visitante visualiza o vídeo de alguma forma. Você pode adicionar classificações para essa variável.

   (**Opcional**) A variável Insight personalizado fornece informações sobre o caminho do vídeo.

   * Tipo de variável: Evar
   * Expiração padrão: visita
   * Insight personalizado (s.prop, usado para caminhos de vídeo)

* **a.media.name**

   (**Opcional**) Fornece informações sobre o caminho do vídeo. Os caminhos devem ser habilitados para esta variável pelo ClientCare.

   * Tipo de evento: Insight personalizado (s.prop).
   * Tipo de variável: Insight personalizado (s. prop)

* **a.media.segment**

   (**Obrigatório**) Coleta dados de segmento do vídeo, incluindo o nome do segmento e a ordem na qual ele ocorre no vídeo.

   Essa variável é preenchida com a habilitação da variável `segmentByMilestones` durante o monitoramento de eventos de player de modo automático, ou ao configurar um nome de segmento personalizado durante o monitoramento manual dos eventos do player. For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the `1:M:0-25` segments eVar.

   O método padrão de coleta de dados de vídeo reúne dados nos seguintes pontos: início do vídeo (reproduzir), início do segmento e fim do vídeo (parar). O sistema conta a primeira exibição de segmento no início, quando o visitante começa a assistir. As exibições de segmento subsequente ocorrem quando o segmento começa.

   * Tipo de variável: Evar
   * Expiração padrão: visualização de página

* **a.contentType**

   Coleta dados sobre o tipo de conteúdo exibido por um visitante. Ocorrências enviadas por meio da avaliação de vídeo recebem um tipo de conteúdo chamado “vídeo”. Essa variável não precisa estar reservada exclusivamente para o rastreamento de vídeo. Quando outros conteúdos relatam o tipo por meio da mesma variável, é possível analisar a distribuição de visitantes em tipos diferentes de conteúdo. Por exemplo, é possível marcar outros tipos de conteúdo por meio de valores como “artigo” ou “página do produto” com essa variável.

   Da perspectiva de avaliação do vídeo, o tipo de conteúdo permite que você identifique visitantes de vídeo e, portanto, calcule as taxas de conversão do vídeo.

   * Tipo de variável: Evar
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

## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

Defina um objeto `MediaSettings` com as configurações que deseja usar para monitorar o vídeo:

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `Play`, `Stop`, and `Close` methods need to be called at the appropriate times. Por exemplo, quando o reprodutor está pausado, `Stop`. `Play` é chamado quando a reprodução começa ou é retomada.

## Classes {#section_16838332727348F990305C0C6B0D795C}

### Classe: MediaSettings

```
property Platform::String ^name; 
property Platform::String ^playerName; 
property Platform::String ^playerID; 
property double length; 
property Platform::String ^channel; 
property Platform::String ^milestones; 
property Platform::String ^offsetMilestones; 
property bool segmentByMilestones; 
property bool segmentByOffsetMilestones; 
property int trackSeconds; 
property int completeCloseOffsetThreshold; 
 
// MediaAnalytics Ad settings 
property Platform::String ^parentName; 
property Platform::String ^parentPod; 
property Platform::String ^CPM; 
property double parentPodPosition; 
property bool isMediaAd;
```

### Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **Settingswith (winjs: Settingswith)**

   Retorna um objeto `MediaSettings` com parâmetros especificados.

   * Esta é a sintaxe para este método:

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name,  double length, Platform::String ^playerName, Platform::String  ^playerID); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      var  mySettings  =  ADB.Media.settingsWith("name", 10,  "playerName", "playerId"); 
      ```

* **Adsettingswith (winjs: Adsettingswith)**

   Retorna um objeto `MediaSettings` para utilizar no monitoramento de um vídeo de anúncio.

   * Esta é a sintaxe para este método:

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name,  double length, Platform::String ^playerName, Platform::String  ^parentName, Platform::String ^parentPod, double parentPosition,  Platform::String ^CPM);
      ```

   * Esta é a amostra de código para este método:

      ```js
      var  myAdSettings = ADB.Media.adSettingsWith("name", 10,  "playerName", "parentName", "parentPod", 5, "myCPM");
      ```

* **Abrir (winjs: open)**

   Rastreia uma abertura de mídia com o uso das configurações definidas em `settings`.

   * Esta é a sintaxe para este método:

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.Media.open(mySettings);
      ```

* **Fechar (winjs: close)**

   Rastreia um fechamento de mídia para o item de mídia chamado *`name`*.

   * Esta é a sintaxe para este método:

      ```csharp
      static  void  Close(Platform::String  ^name);
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.Media.close("mediaName"); 
      ```

* **Reproduzir (winjs: play)**

   Rastreia uma reprodução de mídia para o item de mídia chamado *`name`* no *offset* dado (em segundos).

   * Esta é a sintaxe para este método:

      ```csharp
      static  void  Play(Platform::String ^name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.Media.play("mediaName",  0);
      ```

* **Concluído (winjs: complete)**

   Marca manualmente o item de mídia como concluído no *offset* em questão (em segundos).

   * Esta é a sintaxe para este método:

      ```csharp
      static  void  Complete(Platform::String ^name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.Media.complete("mediaName", 8);
      ```

* **Parar (winjs: stop)**

   Notifica ao módulo de mídia que o vídeo foi interrompido ou pausado no *offset* em questão.

   * Esta é a sintaxe para este método:

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.Media.stop("mediaName",  4);
      ```

* **Clique em (winjs: click)**

   Notifica ao módulo de mídia que o item de mídia foi clicado.

   * Esta é a sintaxe para este método:

      ```csharp
      static void Click(Platform::String ^name, double  offset);
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.Media.click("mediaName",  3); 
      ```

* **Track (winjs: track)**

   Envia uma chamada de ação de rastreamento (sem exibição de página) para o estado de mídia atual.

   * Esta é a sintaxe para este método:

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^,  Platform::Object> ^contextData); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.Media.track("mediaName",  null);
      ```
