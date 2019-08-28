---
description: A variável products não pode ser configurada usando as regras de processamento. No SDK 4.x para iOS, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir products diretamente na chamada do servidor.
seo-description: A variável products não pode ser configurada usando as regras de processamento. No SDK 4.x para iOS, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir products diretamente na chamada do servidor.
seo-title: Variável products
solution: Marketing Cloud, Analytics
title: Variável products
topic: Desenvolvedor e implementação
uuid: 6 ece 4 d 27-ef 86-435 c-a 6 f 7-bd 76 be 1 c 95 ca
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable {#products-variable}

A variável products não pode ser configurada usando as regras de processamento. No SDK 4.x para iOS, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir products diretamente na chamada do servidor.

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value by using the syntax that is defined for the *`products`* variable:

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

Não é necessário mapear a variável *`products`* usando regras de processamento porque é definida diretamente na solicitação de imagem pelo SDK.
