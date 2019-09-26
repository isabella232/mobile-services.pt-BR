---
description: Este é um exemplo da variável products com eVars de merchandising e eventos específicos do produto.
seo-description: Este é um exemplo da variável products com eVars de merchandising e eventos específicos do produto.
seo-title: Variável products com eVars de merchandising e eventos específicos do produto
solution: Marketing Cloud,Analytics
title: Variável products com eVars de merchandising e eventos específicos do produto
topic: Desenvolvedor e implementação
uuid: f913211e-97ad-4237-bfe4-7ded01295caf
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Products variable with merchandising eVars and product-specific events {#products-variable-with-merchandising-evars-and-product-specific-events}

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
>Se você acionar um evento específico do produto usando a *`&&products`* variável, também deverá definir esse evento na *`&&events`* variável. Se você não definir esse evento, ele será filtrado durante o processamento.

