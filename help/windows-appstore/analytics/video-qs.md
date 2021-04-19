---
description: Informações para ajudá-lo com o Video Analytics.
seo-description: Informações para ajudá-lo com o Video Analytics.
seo-title: Análise de vídeo
solution: Experience Cloud,Analytics
title: Análise de vídeo
topic-fix: Developer and implementation
uuid: 7d4e6668-a1d9-41da-96c8-8baac860c5b0
exl-id: 86d70a6f-db12-4f94-a37f-4b1d4b99e0f1
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 72%

---

# Análise de vídeo {#video-analytics}

Informações para ajudá-lo com o Video Analytics.

A medição de vídeo está descrita em detalhes no guia [Medição de áudio e vídeo no Adobe Analytics](https://docs.adobe.com/content/help/pt-BR/media-analytics/using/media-overview.html/). O processo geral para medição de vídeo é muito parecido em todas as plataformas AppMeasurement. Esta seção de início rápido fornece uma visão geral básica das tarefas do desenvolvedor junto com exemplos de código.

A tabela a seguir lista os dados de mídia que são enviados para o Analytics. Usar as regras de processamento para mapear os dados de contexto para uma variável do Analytics.

* **a.media.name**

   (Obrigatório) Coleta o nome do vídeo, conforme especificado na implementação, quando um visitante visualiza o vídeo de alguma forma. É possível adicionar classificações para essa variável.

   (**Opcional**) A variável Insight personalizado fornece informações de definição de caminho de vídeo.

   * Tipo de variável: eVar
   * Expiração padrão: visita
   * Custom Insight (s.prop, usado para definição de caminho de vídeo)

* **a.media.name**

   (Opcional) Fornece informações sobre o caminho do vídeo. O caminho deve ser habilitado para esta variável pelo ClientCare.

   Tipo de evento: Insight personalizado (s.prop)

   * Tipo de variável: Insight personalizado (s.prop)

* **a.media.segment**

   (Obrigatório) Coleta dados de segmento do vídeo, incluindo o nome do segmento e a ordem na qual ele ocorre no vídeo. Essa variável é preenchida com a habilitação da variável `segmentByMilestones` durante o monitoramento de eventos de player de modo automático, ou ao configurar um nome de segmento personalizado durante o monitoramento manual dos eventos do player. Por exemplo, quando um visitante exibe o primeiro segmento em um vídeo, o SiteCatalyst pode coletar as seguintes informações no eVar do segmento `1:M:0-25`.

   O método padrão de coleta de dados de vídeo coleta dados nos seguintes pontos:

   * início do vídeo (reproduzir)
   * início do segmento
   * fim do vídeo (parar)

   O Analytics conta a primeira visualização de segmento no início do segmento, quando o visitante começa a assistir. As visualizações de segmento subsequentes ocorrem conforme o segmento começa.

   * Tipo de variável: eVar
   * Expiração padrão: visualização de página


* **a.contentType**

   Coleta dados sobre o tipo de conteúdo exibido por um visitante. Ocorrências enviadas por avaliação de vídeo recebem um tipo de conteúdo de &quot;vídeo&quot;. Essa variável não precisa ser reservada exclusivamente para rastreamento de vídeo. Quando outros conteúdos relatam o tipo por meio da mesma variável, é possível analisar a distribuição de visitantes em tipos diferentes de conteúdo. Por exemplo, é possível marcar outros tipos de conteúdo por meio de valores como “artigo” ou “página do produto” com essa variável. Da perspectiva de avaliação do vídeo, o tipo de conteúdo permite que você identifique visitantes de vídeo e calcule as taxas de conversão do vídeo.

   * Tipo de variável: eVar
   * Expiração padrão: visualização de página

* **a.media.timePlayed**

   Contabiliza o tempo, em segundos, que é gasto com a exibição de um vídeo desde o último processo de coleta de dados (solicitação da imagem).

   * Tipo de variável: Evento
   * Tipo: contador

* **a.media.view**

   Indica que um visitante visualizou uma parte de um de vídeo. No entanto, não fornece informações sobre quanto ou qual parte de um vídeo o visitante visualizou.

   * Variável: Evento
   * Tipo: contador

* **a.media.segmentView**

   Indica que um visitante visualizou uma parte de um segmento de vídeo. No entanto, não fornece informações sobre quanto ou qual parte de um vídeo o visitante visualizou.

   * Tipo de variável: Evento
   * Tipo: contador

* **a .media.complete**

   Indica se o usuário exibiu um vídeo completo. Por padrão, o evento completo é avaliado um segundo antes do fim do vídeo. Durante a implementação, é possível especificar quantos segundos a partir do fim do vídeo são necessários para considerar a visualização como concluída. Para vídeos ao vivo e outras transmissões que não têm um fim definido, você pode especificar um ponto personalizado para medir as conclusões. Por exemplo, depois de um tempo de exibição específico.

   * Tipo de variável: Evento
   * Tipo: contador


## Definir as configurações de mídia {#section_929945D4183C428AAF3B983EFD3E2500}

Defina um objeto `MediaSettings` com as configurações que deseja usar para monitorar o vídeo:

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## Rastrear eventos de vídeo {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Para avaliar a reprodução de vídeo, os métodos `Play`, `Stop`, e `Close` devem ser chamados em momentos apropriados. Por exemplo, quando o reprodutor está pausado, `Stop`. `Play` é chamado quando a reprodução começa ou é retomada.

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

## Referência de método e classe de medição de mídia {#section_50DF9359A7B14DF092634C8E913C77FE}

* **SettingsWith (winJS: settingsWith)**

   Retorna um objeto `MediaSetting` com parâmetros especificados.

   * Esta é a sintaxe para este método:

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^playerID); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId"); 
      ```

* **AdSettingsWith (winJS: adSettingsWith**

   Retorna um objeto `MediaSettings` para utilizar no monitoramento de um vídeo de anúncio.

   * Esta é a sintaxe para este método:

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^parentName, Platform::String ^parentPod, double parentPosition, Platform::String ^CPM); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      var myAdSettings = ADB.Media.adSettingsWith("name", 10, "playerName", "parentName", "parentPod", 5, "myCPM"); 
      ```

* **Open (winJS: open)**

   Rastreia uma abertura de mídia usando as configurações definidas em `settings`.

   * Esta é a sintaxe para este método:

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.Media.open(mySettings); 
      ```

* **Close (winJS: fechar)**

   Rastreia um fechamento de mídia para o item de mídia chamado *name*.

   * Esta é a sintaxe para este método:

      ```csharp
      static void Close(Platform::String ^name);
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.Media.close("mediaName");
      ```

* **Play (winJS: play)**

   Rastreia uma reprodução de mídia para o item de mídia chamado *`name`* no *offset* especificado (em segundos).

   * Esta é a sintaxe para este método:

      ```csharp
      static void Play(Platform::String ^name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.Media.play("mediaName", 0);
      ```

* **Complete (winJS: complete)**

   Marca manualmente o item de mídia como concluído no *offset* em questão (em segundos).

   * Esta é a sintaxe para este método:

      ```csharp
      static void Complete(Platform::String ^name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.Media.complete("mediaName", 8); 
      ```

* **Stop (winJS: stop)**

   Notifica ao módulo de mídia que o vídeo foi interrompido ou pausado no *offset* em questão.

   * Esta é a sintaxe para este método:

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.Media.stop("mediaName", 4);
      ```

* **Clique em (winJS: click)**

   Notifica ao módulo de mídia que o item de mídia foi clicado.

   * Esta é a sintaxe para este método:

      ```csharp
      static void Click(Platform::String ^name, double offset);
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.Media.click("mediaName", 3);
      ```

* **Track (winJS: track)**

   Envia uma chamada de ação de rastreamento (sem exibição de página) para o estado de mídia atual.

   * Esta é a sintaxe para este método:

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADB.Media.track("mediaName", null);
      ```
