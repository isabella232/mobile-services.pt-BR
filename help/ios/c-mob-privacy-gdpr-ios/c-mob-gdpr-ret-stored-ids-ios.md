---
description: Essas informações o ajudam a recuperar identidades de SDK da Experience Cloud armazenadas localmente do aplicativo iOS e com solicitações de acesso a dados do GDPR.
seo-description: Essas informações o ajudam a recuperar identidades de SDK da Experience Cloud armazenadas localmente do aplicativo iOS e com solicitações de acesso a dados do GDPR.
seo-title: Recuperando Identificadores Armazenados
title: Recuperando Identificadores Armazenados
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 69%

---


# Recuperar identificadores armazenados{#retrieving-stored-identifiers}

Essas informações o ajudam a recuperar identidades de SDK da Experience Cloud armazenadas localmente do aplicativo iOS e com solicitações de acesso a dados do GDPR.

Para obter mais informações sobre o RGPD, consulte o [RGPD e a sua empresa](https://www.adobe.com/br/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>O método `getAllIdentifiersAsync` recupera identidades armazenadas nos SDKs da Experience Cloud. You must call this method **before** the user opts-out.

Identidades de SDK de Experience Cloud (se aplicável) são armazenadas localmente e retornam em uma sequência de caracteres JSON, que pode conter:

* Contexto da empresa - IDs de organização IMS
* IDs de usuário
* Experience Cloud ID (MID), anteriormente conhecida como Experience Cloud ID
* Códigos de integração (ADID, ID de push)
* IDs de fonte de dados (DPID, DPUUID)
* IDs do Analytics (AVID, AID, VID e RSIDs associados)
* IDs herdadas do público alvo (TNTID, TNT3rdpartyID)
* ID do Audience Manager (UUID)

A seguir encontra-se um exemplo do método `ADBMobile getAllIdentifiersAsync` no iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

