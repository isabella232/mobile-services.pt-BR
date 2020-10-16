---
description: Este é um exemplo da variável products com eVars de merchandising e eventos específicos do produto.
keywords: android;library;mobile;sdk
seo-description: Este é um exemplo da variável products com eVars de merchandising e eventos específicos do produto.
seo-title: Variável products com eVars de merchandising e eventos específicos do produto
solution: Experience Cloud,Analytics
title: Variável products com eVars de merchandising e eventos específicos do produto
topic: Developer and implementation
uuid: 64f822a0-6ccf-48e7-8886-31b93d8198a3
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '98'
ht-degree: 100%

---


# Variável products com eVars de merchandising e eventos específicos do produto {#products-variable-with-merchandising-evars-and-product-specific-events}

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
>Se você acionar um evento específico do produto usando a variável *`&&products`*, também deverá definir esse evento na variável *`&&events`*. Se você não definir esse evento, ele será filtrado durante o processamento.

