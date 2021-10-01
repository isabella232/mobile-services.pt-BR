---
description: Essas informações o ajudam a recuperar identidades de SDK armazenadas localmente do aplicativo Android e com solicitações de acesso a dados do GDPR.
title: Recuperar identificadores armazenados
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
exl-id: 86c990d8-334b-4003-b0ac-d5404cb598e4
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 72%

---

# Recuperar identificadores armazenados{#retrieving-stored-identifiers}

Essas informações o ajudam a recuperar identidades de SDK armazenadas localmente do aplicativo Android e com solicitações de acesso a dados do GDPR.

>[!IMPORTANT]
>
>O método `getAllIdentifiersAsync` recupera identidades armazenadas no SDK. Você deve chamar esse método **antes de** o usuário recusar.

Identidades de SDK (se aplicável) são armazenadas localmente e retornam em uma sequência JSON, que pode conter:

* Contexto da empresa - IDs de organização IMS
* IDs de usuário
* Experience Cloud ID (MID), anteriormente conhecida como Experience Cloud ID
* Códigos de integração (ADID, Push ID)
* IDs de fonte de dados (DPID, DPUUID)
* IDs do Analytics (AVID, AID, VID e RSIDs associados)
* IDs herdadas do Target (TNTID, TNT3rdpartyID)
* ID do Audience Manager (UUID)

A seguir encontra-se um exemplo do método `ADBMobile getAllIdentifiersAsync` no Android:

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```
