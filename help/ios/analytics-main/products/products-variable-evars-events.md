---
description: Este é um exemplo da variável products com eVars de merchandising e eventos específicos do produto.
seo-description: Este é um exemplo da variável products com eVars de merchandising e eventos específicos do produto.
seo-title: Variável products com eVars de merchandising e eventos específicos do produto
solution: Experience Cloud,Analytics
title: Variável products com eVars de merchandising e eventos específicos do produto
topic: Developer and implementation
uuid: f913211e-97ad-4237-bfe4-7ded01295caf
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '98'
ht-degree: 100%

---


# Variável products com eVars de merchandising e eventos específicos do produto {#products-variable-with-merchandising-evars-and-product-specific-events}

Este é um exemplo da variável products com eVars de merchandising e eventos específicos do produto.

```
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@"event1" forKey:@"&&events"]; 
[contextData setObject:@";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData];
```

>[!TIP]
>
>Se você acionar um evento específico do produto usando a variável *`&&products`*, também deverá definir esse evento na variável *`&&events`*. Se você não definir esse evento, ele será filtrado durante o processamento.

