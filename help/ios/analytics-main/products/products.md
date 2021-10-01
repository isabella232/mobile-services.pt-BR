---
description: A variável products não pode ser definida usando regras de processamento. No SDK 4.x do iOS, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir produtos diretamente na chamada do servidor.
solution: Experience Cloud,Analytics
title: Variável products
topic-fix: Developer and implementation
uuid: 6ece4d27-ef86-435c-a6f7-bd76be1c95ca
exl-id: c945add4-5358-44f6-b445-554b0df056c1
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 100%

---

# Variável products  {#products-variable}

A variável products não pode ser definida usando regras de processamento. No SDK 4.x do iOS, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir produtos diretamente na chamada do servidor.

Para configurar a variável *`products`*, defina uma chave de dados de contexto para `"&&products"` e defina o valor usando a sintaxe definida para a variável *`products`*:

```objective-c
[contextData setObject:@"Category;Product;Quantity;Price[,Category;Product;Quantity;Price]" forKey:@"&&products"];
```

Por exemplo:

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@";Running Shoes;1;69.95,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData]; 
```

*`products`* é definida diretamente na solicitação de imagem e as outras variáveis são definidas como dados de contexto. Todas as variáveis de dados de contexto devem ser mapeadas usando as regras de processamento:

![](assets/map-products.png)

Não é necessário mapear a variável  *`products`* usando regras de processamento, porque é definida diretamente na solicitação de imagem pelo SDK.
