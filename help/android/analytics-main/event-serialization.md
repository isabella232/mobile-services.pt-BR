---
description: A serialização de eventos não é suportada pelas regras de processamento. No SDK móvel, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.
keywords: android;library;mobile;sdk
seo-description: A serialização de eventos não é suportada pelas regras de processamento. No SDK móvel, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.
seo-title: Serialização de eventos
solution: Marketing Cloud,Analytics
title: Serialização de eventos
topic: Desenvolvedor e implementação
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Serialização de eventos {#event-serialization}

A serialização de eventos não é suportada pelas regras de processamento. No SDK móvel, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.

```java
cdata.put("&&events", "event1:12341234");
```

Por exemplo:

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add events 
cdata.put("&&events", "event1:12341234"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("action", cdata); 
// trackState example: 
Analytics.trackState("State Name", cdata);
```

