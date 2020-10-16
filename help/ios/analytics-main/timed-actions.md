---
description: As ações cronometradas permitem medir o tempo no aplicativo e o tempo total entre o início e o fim de uma ação. O SDK calcula a quantidade de tempo em cada sessão e o tempo total entre sessões que levará para a ação ser concluída. É possível usar as ações cronometradas para definir segmentos e comparar o tempo de compra, o nível de passagem, o fluxo de finalização da compra e assim por diante.
seo-description: As ações cronometradas permitem medir o tempo no aplicativo e o tempo total entre o início e o fim de uma ação. O SDK calcula a quantidade de tempo em cada sessão e o tempo total entre sessões que levará para a ação ser concluída. É possível usar as ações cronometradas para definir segmentos e comparar o tempo de compra, o nível de passagem, o fluxo de finalização da compra e assim por diante.
seo-title: Ações cronometradas
solution: Experience Cloud,Analytics
title: Ações cronometradas
topic: Developer and implementation
uuid: dbcbac5a-6345-49f6-b050-0db05292f005
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '403'
ht-degree: 100%

---


# Ações cronometradas {#timed-actions}

As ações cronometradas permitem medir o tempo no aplicativo e o tempo total entre o início e o fim de uma ação. O SDK calcula a quantidade de tempo em cada sessão e o tempo total entre sessões que levará para a ação ser concluída. É possível usar as ações cronometradas para definir segmentos e comparar o tempo de compra, o nível de passagem, o fluxo de finalização da compra e assim por diante.

As seguintes métricas são reportadas para ações cronometradas:

* Número total de segundos no aplicativo entre o início e o término - sessões cruzadas
* Número total de segundos entre o início e o término (hora do relógio)

Um retorno de chamada opcional permite executar ações adicionais quando a ação cronometrada é concluída:

* Execute o código e adicione qualquer lógica - lógica personalizada opcional com base nos resultados de duração.
* Adicione dados de contexto antes de transmitir as durações.
* Cancele a ocorrência e as durações ainda não enviadas.

## Rastreamento de ações cronometradas {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao seu projeto* em [Implementação principal e ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe a biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Chame `trackTimedActionStart` e forneça um nome de ação cronometrada e dados de contexto opcionais.

   ```objective-c
   [ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                               data:@{@"ExperienceName" : experience}];
   ```

1. (Opcional) Para adicionar dados de contexto adicionais, é possível chamar `trackTimedActionUpdate` com o nome da ação agendada.

   ```objective-c
   [ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                                data:@{@"myapp.ImageLiked" : imageName}];
   ```

1. Quando o evento for concluído, faça uma chamada para `trackTimedActionEnd` e passe o nome da ação agendada e `TimedActionBlock` (chamada de retorno) que verificará todos os dados e calculará as durações.

   As métricas de eventos cronometrados são salvas em variáveis da solução móvel para relatórios automáticos.

   ```objective-c
   [ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                            logic:nil];
   ```

## Envio de dados adicionais {#section_3EBE813E54A24F6FB669B2478B5661F9}

Além do nome da ação cronometrada, você pode enviar dados de contexto adicionais com as chamadas de ação de atualização e de início:

```objective-c
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"myapp.ImageLiked" : imageName}];
```

Os valores dos dados de contexto devem ser mapeados para variáveis personalizadas:

![](assets/map-variable-context-ltv.png)

## Exemplo {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```objective-c
// Timed Action Start Example 
[ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                            data:@{@"ExperienceName" : experience}];

// Timed Action Update Example 
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"ImageLiked" : imageName}];

// Timed Action End Example 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:nil]; 
 
// Timed Action End Example with Callback 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:^BOOL(NSTimeInterval inAppDuration,  
                                     NSTimeInterval totalDuration,  
                                     NSMutableDictionary *data) { 
                                        [data setObject:@"PurchaseItem" forKey:@"Item453"]; 
                                        return YES; //return YES to send the hit, NO to cancel 
                                     }];
```

