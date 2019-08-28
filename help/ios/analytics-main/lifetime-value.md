---
description: O valor de tempo de vida permite medir e atingir um valor para cada usuário.
seo-description: O valor de tempo de vida permite medir e atingir um valor para cada usuário.
seo-title: Valor do tempo de vida do visitante
solution: Marketing Cloud, Analytics
title: Valor do tempo de vida do visitante
topic: Desenvolvedor e implementação
uuid: d 830 d 18 b -4313-43 bb -8 d 75-3789869 d 0 f 1 d
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visitor lifetime value {#visitor-lifetime-value}

O valor de tempo de vida permite medir e atingir um valor para cada usuário.

Cada vez que um valor é enviado com `trackLifetimeValueIncrease`, o valor é adicionado ao valor existente. O valor de tempo de vida é armazenado no dispositivo e pode ser recuperado a qualquer momento ao chamar `lifetimeValue`. Isso pode ser usado para armazenar compras de tempo de vida, exibições de anúncios, conclusões de vídeos, compartilhamentos nas redes sociais, carregamentos de fotos e assim por diante.

## Track the visitor lifetime value {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o Arquivo de configuração ao projeto* na [Implementação principal e no ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe a biblioteca:

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. Chame `trackLifetimeValueIncrease` com o montante para aumentar o valor:

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Além do valor de tempo de vida, você pode enviar dados de contexto adicionais com cada chamada de ação de rastreamento:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

Os valores de dados de contexto devem ser mapeados para variáveis personalizadas:

![](assets/map-variable-context-ltv.png)

