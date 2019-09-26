---
description: Não é possível definir a variável products usando as regras de processamento. No SDK para dispositivos móveis, deve-se usar uma sintaxe especial no parâmetro de dados de contexto para definir products diretamente na chamada do servidor.
seo-description: Não é possível definir a variável products usando as regras de processamento. No SDK para dispositivos móveis, deve-se usar uma sintaxe especial no parâmetro de dados de contexto para definir products diretamente na chamada do servidor.
seo-title: Products variable
solution: Marketing Cloud,Analytics
title: Variável products
topic: Desenvolvedor e implementação
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable{#products-variable}

Não é possível definir a variável products usando as regras de processamento. No SDK para dispositivos móveis, deve-se usar uma sintaxe especial no parâmetro de dados de contexto para definir products diretamente na chamada do servidor.

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value using the syntax defined for the *`products`*:

```js
cdata["&&products"] = "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]";
```

Por exemplo:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&products"] = ";Running Shoes;1;69.95,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

*`products`* é definida diretamente na solicitação de imagem e as outras variáveis são definidas como dados de contexto. Todas as variáveis de dados de contexto devem ser mapeadas com o uso das regras de processamento:

![](assets/products-procrules.png)

You do not need to map the *`products`* variable using processing rules since it is set directly on the image request by the SDK.
