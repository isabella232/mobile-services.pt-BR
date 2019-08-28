---
description: Este é um exemplo da variável products com eVars de merchandising e eventos específicos do produto.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: Este é um exemplo da variável products com eVars de merchandising e eventos específicos do produto.
seo-title: Variável products com eVars de merchandising e eventos específicos do produto
solution: Marketing Cloud, Analytics
title: Variável products com eVars de merchandising e eventos específicos do produto
topic: Desenvolvedor e implementação
uuid: 64 f 822 a 0-6 ccf -48 e 7-8886-31 b 93 d 8198 a 3
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Products variable with merchandising eVars and product-specific events {#products-variable-with-merchandising-evars-and-product-specific-events}

Este é um exemplo da variável products com eVars de merchandising e eventos específicos do produto.

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&events", "event1"); 
cdata.put("&&products", ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>Se você acionar um evento específico do produto usando *`&&products`* a variável, também deverá definir esse evento na *`&&events`* variável. Se você não definir esse evento, ele será filtrado durante o processamento.

