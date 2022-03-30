---
description: A variável products não pode ser definida usando as regras de processamento. No SDK móvel, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir produtos diretamente na chamada do servidor.
solution: Experience Cloud Services,Analytics
title: 'Variável products '
topic-fix: Developer and implementation
uuid: 607983d6-48ac-4274-bfc8-b1ca4e5dad1b
exl-id: 0575236c-9858-4bf9-a2ce-6e2667d58ddd
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 7%

---

# Variável products  {#products-variable}

A variável products não pode ser definida usando as regras de processamento. No SDK móvel, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir produtos diretamente na chamada do servidor.

Para definir a variável *`products`* , defina uma chave de dados de contexto para `"&&products"`e defina o valor usando a sintaxe definida para *`products` variável:

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

O *`products`* é definida diretamente na solicitação de imagem e as outras variáveis são definidas como dados de contexto. Todas as variáveis de dados de contexto devem ser mapeadas usando as regras de processamento:

![](assets/products-procrules.png)

Não é necessário mapear a variável *`products`* usando regras de processamento, pois é definida diretamente na solicitação de imagem pelo SDK.

## Variável products com eVars de merchandising e eventos específicos do produto {#section_685D53AD3D064F9A8E225F995A9BA545}

Um exemplo da variável *`products`* com eVars de merchandising e eventos específicos do produto.

```
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&events"] = "event1 "; 
cdata["&&products"] = ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
  
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>Se você acionar um evento específico do produto usando a variável *`&&products`* , você também deve definir esse evento na variável *`&&events`* caso contrário, o evento será filtrado durante o processamento.
