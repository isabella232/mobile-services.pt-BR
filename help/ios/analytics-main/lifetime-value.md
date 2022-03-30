---
description: O valor de tempo de vida permite medir e atingir um valor para cada usuário.
solution: Experience Cloud Services,Analytics
title: Valor vitalício do visitante
topic-fix: Developer and implementation
uuid: d830d18b-4313-43bb-8d75-3789869d0f1d
exl-id: f1b684b1-9919-400d-a88a-6d4a0809d9e1
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 100%

---

# Valor vitalício do visitante {#visitor-lifetime-value}

O valor de tempo de vida permite medir e atingir um valor para cada usuário.

Cada vez que um valor é enviado com `trackLifetimeValueIncrease`, o valor é adicionado ao valor existente. O valor de tempo de vida é armazenado no dispositivo e pode ser recuperado a qualquer momento ao chamar `lifetimeValue`. Isso pode ser usado para armazenar compras de tempo de vida, exibições de anúncios, conclusões de vídeos, compartilhamentos nas redes sociais, carregamentos de fotos e assim por diante.

## Rastrear o valor vitalício do visitante {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao seu projeto* em [Implementação principal e ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe a biblioteca:

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. Chame `trackLifetimeValueIncrease` com o montante para aumentar o valor:

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## Enviar dados adicionais {#section_3EBE813E54A24F6FB669B2478B5661F9}

Além do valor de tempo de vida, você pode enviar dados de contexto adicionais com cada chamada de ação de rastreamento:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

Os valores dos dados de contexto devem ser mapeados para variáveis personalizadas:

![](assets/map-variable-context-ltv.png)
