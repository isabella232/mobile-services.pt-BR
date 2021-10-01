---
description: Essas informações o ajudam a recuperar identidades de SDK da Experience Cloud armazenadas localmente do aplicativo iOS e com solicitações de acesso a dados do GDPR.
title: Recuperar identificadores armazenados
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
exl-id: ec8592af-fb08-4ab3-99a1-51ac5697a3d8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 67%

---

# Recuperar identificadores armazenados{#retrieving-stored-identifiers}

Essas informações o ajudam a recuperar identidades de SDK da Experience Cloud armazenadas localmente do aplicativo iOS e com solicitações de acesso a dados do GDPR.

Para obter mais informações sobre o GDPR, consulte [GDPR e a sua empresa](https://www.adobe.com/br/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>O método `getAllIdentifiersAsync` recupera identidades armazenadas nos SDKs da Experience Cloud. Você deve chamar esse método **antes de** o usuário recusar.

As identidades de SDK do Experience Cloud (conforme aplicável) são armazenadas localmente e retornam em uma sequência JSON, que pode conter:

* Contexto da empresa - IDs de organização IMS
* IDs de usuário
* Experience Cloud ID (MID), anteriormente conhecida como Experience Cloud ID
* Códigos de integração (ADID, Push ID)
* IDs de fonte de dados (DPID, DPUUID)
* IDs do Analytics (AVID, AID, VID e RSIDs associados)
* IDs herdadas do Target (TNTID, TNT3rdpartyID)
* ID do Audience Manager (UUID)

A seguir encontra-se um exemplo do método `ADBMobile getAllIdentifiersAsync` no iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```
