---
description: A variável products não pode ser definida usando as regras de processamento. No SDK móvel, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir produtos diretamente na chamada do servidor.
solution: Experience Cloud,Analytics
title: 'Variável products '
topic-fix: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
exl-id: b731e794-7134-4c6d-a41b-09ac9b84763d
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 15%

---

# Variável products {#products-variable}

A variável products não pode ser definida usando as regras de processamento. No SDK móvel, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir produtos diretamente na chamada do servidor.

Para definir a variável *`products`*, defina uma chave de dados de contexto para `"&&products"` e defina o valor usando a sintaxe definida para *`products`*:

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

*`products`* é definida diretamente na solicitação de imagem e as outras variáveis são definidas como dados de contexto. Todas as variáveis de dados de contexto devem ser mapeadas usando as regras de processamento:

![](assets/products-procrules.png)

Não é necessário mapear a variável *`products`* usando regras de processamento, pois ela é definida diretamente na solicitação de imagem pelo SDK.
