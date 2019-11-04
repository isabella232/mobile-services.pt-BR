---
description: A serialização de eventos não é suportada pelas regras de processamento. No SDK móvel, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.
seo-description: A serialização de eventos não é suportada pelas regras de processamento. No SDK móvel, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.
seo-title: Serialização de eventos
solution: Experience Cloud,Analytics
title: Serialização de eventos
topic: Desenvolvedor e implementação
uuid: 19a27df4-0998-403d-800c-26ff61149208
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Serialização de eventos {#event-serialization}

A serialização de eventos não é suportada pelas regras de processamento. No SDK móvel, é necessário usar uma sintaxe especial no parâmetro de dados de contexto para definir eventos serializados diretamente na chamada do servidor.

```objective-c
[contextData setObject:@"eventN:serial number" forKey:@"&&events"];
```

Por exemplo:

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add events 
[contextData setObject:@"event1:12341234" forKey:@"&&events"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"action" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"State Name" data:contextData]; 
```

