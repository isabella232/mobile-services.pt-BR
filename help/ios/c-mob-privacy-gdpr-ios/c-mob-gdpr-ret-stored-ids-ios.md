---
description: Essas informações o ajudam a recuperar identidades de SDK da Experience Cloud armazenadas localmente do aplicativo iOS e com solicitações de acesso a dados do GDPR.
seo-description: Essas informações o ajudam a recuperar identidades de SDK da Experience Cloud armazenadas localmente do aplicativo iOS e com solicitações de acesso a dados do GDPR.
seo-title: Recuperar identificadores armazenados
title: Recuperar identificadores armazenados
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Retrieving stored identifiers{#retrieving-stored-identifiers}

Essas informações o ajudam a recuperar identidades de SDK da Experience Cloud armazenadas localmente do aplicativo iOS e com solicitações de acesso a dados do GDPR.

Para obter mais informações sobre o GDPR, consulte [GDPR e seus negócios](https://www.adobe.com/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>The `getAllIdentifiersAsync` method retrieves identities that are stored in the Experience Cloud SDKs. Você deve chamar esse método **antes** que usuário saia.

As identidades de SDK da Experience Cloud (se for o caso) são armazenadas localmente e retornam em um arquivo JSON, que pode conter:

* Contexto da empresa - IDs de org IMS
* IDs de usuário
* Experience Cloud ID (MID), anteriormente conhecida como Marketing Cloud ID
* Códigos de integração (ADID, Push ID)
* IDs da fonte de dados (DPID, DPUUID)
* Analytics IDs (AVID, AID, VID e RSIDs associados)
* IDs herdadas do Target (TNTID, TNT3rdpartyID)
* Audience Manager ID (UUID)

A seguir encontra-se um exemplo do método `ADBMobile getAllIdentifiersAsync` no iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

