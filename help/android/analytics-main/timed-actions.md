---
description: As ações cronometradas permitem medir o tempo no aplicativo e o tempo total entre o início e o fim de uma ação. O SDK calcula a quantidade de tempo em cada sessão e o tempo total em todas as sessões que levará para a ação ser concluída. É possível usar as ações cronometradas para definir segmentos e comparar o tempo de compra, o nível de passagem, o fluxo de finalização da compra e assim por diante.
seo-description: As ações cronometradas permitem medir o tempo no aplicativo e o tempo total entre o início e o fim de uma ação. O SDK calcula a quantidade de tempo em cada sessão e o tempo total em todas as sessões que levará para a ação ser concluída. É possível usar as ações cronometradas para definir segmentos e comparar o tempo de compra, o nível de passagem, o fluxo de finalização da compra e assim por diante.
seo-title: Ações cronometradas
solution: Experience Cloud,Analytics
title: Ações cronometradas
topic-fix: Developer and implementation
uuid: 5a48a580-b942-4e49-9f1b-078fea7fccdb
exl-id: d9851440-6e65-4d89-a6b3-81c8abd2bf06
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 100%

---

# Ações cronometradas {#timed-actions}

As ações cronometradas permitem medir o tempo no aplicativo e o tempo total entre o início e o fim de uma ação. O SDK calcula a quantidade de tempo em cada sessão e o tempo total em todas as sessões que levará para a ação ser concluída. É possível usar as ações cronometradas para definir segmentos e comparar o tempo de compra, o nível de passagem, o fluxo de finalização da compra e assim por diante.

As seguintes métricas são reportadas para ações cronometradas:

* Número total de segundos no aplicativo entre o início e o término (sessões cruzadas)
* Número total de segundos entre o início e o término (hora do relógio)

Um retorno de chamada opcional permite executar ações adicionais quando a ação cronometrada é concluída:

* Execute o código e adicione qualquer lógica - lógica personalizada opcional com base nos resultados de duração.
* Adicione dados de contexto antes de transmitir as durações.
* Cancele a ocorrência e as durações ainda não enviadas.

## Rastrear ações cronometradas {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto IntelliJ IDEA ou Eclipse* na [implementação principal e no ciclo de vida](/help/android/getting-started/dev-qs.md).
1. Importe a biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Chame `trackTimedActionStart` e forneça um nome de ação cronometrada e dados de contexto opcionais.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("ExperienceName", experience); 
   Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
   ```

1. (Opcional) Em qualquer ponto, você pode chamar `trackTimedActionUpdate` com o nome da ação cronometrada para acrescentar dados de contexto adicionais.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("myapp.ImageLiked", imageName); 
   Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
   ```

1. Quando o evento for concluído, faça uma chamada para `trackTimedActionEnd` e passe o nome da ação agendada e `TimedActionBlock` (chamada de retorno) que verificará todos os dados e calculará as durações.

   ```java
   Analytics.trackTimedActionEnd("TimeUntilPurchase", cdata);
   ```

   As métricas de eventos cronometrados são salvas em variáveis da solução móvel para relatórios automáticos.

## Envio de dados adicionais {#section_3EBE813E54A24F6FB669B2478B5661F9}

Além disso, em adição ao nome da ação programada, é possível enviar dados de contexto adicionais com o início da ação e as chamadas de atualização de ação:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
```

Os valores de dados de contexto devem ser mapeados para variáveis personalizadas nos Adobe Mobile Services:

![](assets/map-variable-context-ltv.png)

## Exemplos {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```java
// Timed Action Start Example 
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("ExperienceName", experience); 
Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
 
// Timed Action Update Example 
cdata = new HashMap<String, Object>(); 
cdata.put("ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata); 
 
// Timed Action End Example 
Analytics.trackTimedActionEnd("TimeUntilPurchase", null); 
 
// Timed Action End Example with Callback 
Analytics.trackTimedActionEnd("TimeUntilPurchase", new Analytics.TimedActionBlock<Boolean>() { 
 @Override 
 public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) { 
  contextData.put("PurchaseItem", "Item453"); 
  return true; // return true to send the hit, false to cancel 
 } 
});
```
