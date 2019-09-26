---
description: A serialização de eventos não é suportada pelas regras de processamento. No SDK para dispositivos móveis, deve-se usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.
seo-description: A serialização de eventos não é suportada pelas regras de processamento. No SDK para dispositivos móveis, deve-se usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.
seo-title: Serialização de eventos
solution: Marketing Cloud,Analytics
title: Serialização de eventos
topic: Desenvolvedor e implementação
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
translation-type: tm+mt
source-git-commit: 4faf66df50c8b65198fd139bb15927fc2c2849bc

---


# Serialização de eventos{#event-serialization}

A serialização de eventos não é suportada pelas regras de processamento. No SDK móvel, você deve usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.

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

