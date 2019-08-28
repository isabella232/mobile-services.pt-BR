---
description: A serialização de eventos não é suportada pelas regras de processamento. No SDK para dispositivos móveis, deve-se usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.
seo-description: A serialização de eventos não é suportada pelas regras de processamento. No SDK para dispositivos móveis, deve-se usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.
seo-title: Serialização de eventos
solution: Marketing Cloud, Analytics
title: Serialização de eventos
topic: Desenvolvedor e implementação
uuid: 7220 a 001-1174-4013-91 ff-e 8603 d 8 ab 265
translation-type: tm+mt
source-git-commit: f5ba33fe805c502b8ae91ddafcaa0b57e68704b8

---


# Serialização de eventos {#event-serialization}

A serialização de eventos não é suportada pelas regras de processamento. No SDK móvel, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.

```js
cdata["&&events"] = "event1:12341234";
```

Por exemplo:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add events 
cdata["&&events"] = "event1:12341234"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("action", cdata); 
// trackState example: 
ADB.Analytics.trackState("State Name", cdata);
```

