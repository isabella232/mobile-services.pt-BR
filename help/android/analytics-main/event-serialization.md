---
description: A serialização de eventos não é aceita pelas regras de processamento. No SDK móvel, você deve usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.
keywords: android;biblioteca;móvel;sdk
seo-description: A serialização de eventos não é aceita pelas regras de processamento. No SDK móvel, você deve usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.
seo-title: Serialização de eventos
solution: Experience Cloud,Analytics
title: Serialização de eventos
topic-fix: Developer and implementation
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
exl-id: 03556912-fdcc-402e-b1de-233771f4e719
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 100%

---

# Serialização de eventos {#event-serialization}

A serialização de eventos não é aceita pelas regras de processamento. No SDK móvel, você deve usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.

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
