---
description: Essas informações o ajudam a recuperar identidades de SDK armazenadas localmente do aplicativo Android e com solicitações de acesso a dados do GDPR.
seo-description: Essas informações o ajudam a recuperar identidades de SDK armazenadas localmente do aplicativo Android e com solicitações de acesso a dados do GDPR.
seo-title: Recuperar identificadores armazenados
title: Recuperar identificadores armazenados
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Recuperar identificadores armazenados{#retrieving-stored-identifiers}

Essas informações o ajudam a recuperar identidades de SDK armazenadas localmente do aplicativo Android e com solicitações de acesso a dados do GDPR.

>[!IMPORTANT]
>
>O método `getAllIdentifiersAsync` recupera identidades armazenadas no SDK. Você deve chamar esse método **antes** que usuário saia.

Identidades de SDK (se for o caso) são armazenadas localmente e retornam em uma sequência de caracteres JSON, que pode conter:

* Contexto da empresa - IDs de org IMS
* IDs de usuário
* Experience Cloud ID (MID), anteriormente conhecida como Experience Cloud ID
* Códigos de integração (ADID, Push ID)
* IDs da fonte de dados (DPID, DPUUID)
* Analytics IDs (AVID, AID, VID e RSIDs associados)
* IDs herdadas do Target (TNTID, TNT3rdpartyID)
* Audience Manager ID (UUID)

A seguir encontra-se um exemplo do método `ADBMobile getAllIdentifiersAsync` no Android:

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```
