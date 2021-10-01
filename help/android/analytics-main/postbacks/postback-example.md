---
description: É possível usar essas informações para ajudá-lo a entender os postbacks e como eles funcionam.
keywords: android;biblioteca;móvel;sdk
solution: Experience Cloud,Analytics
title: Exemplo de postbacks
topic-fix: Developer and implementation
uuid: 8010cd00-d42b-4e16-8403-692fab2550f1
exl-id: 2ff41066-e2ee-425f-8aff-e5e3f3e5f0f5
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 100%

---

# Exemplo de postbacks {#postbacks-example}

Você pode usar essas informações para entender os postbacks e como eles funcionam.

>[!CAUTION]
>
>Este exemplo é fornecido apenas para fins informativos. O arquivo `ADBMobileConfig.json` deve ser configurado na interface do usuário do Adobe Mobile e não deve ser modificado manualmente. Um arquivo de configuração editado manualmente pode ser perigoso quando a configuração remota de mensagens estiver habilitada.

## `ADBMobileConfig.json` definição {#section_8751E8176F3546C09420341A39758AFF}

```js
"messages": [ 
    { 
        "messageId": "79ae37c9-89b9-465e-af7f-d3351771f1dc", 
        "template": "callback", 
        "payload": {  
            "templateurl": "https://my.server.com/?user={user.name}&zip={user.zip}&c16={%sdkver%}&c27=cln,{a.PrevSessionLength}", 
            "templatebody": "c2RrdmVyPXslc2RrdmVyJX0mY2I9eyVjYWNoZWJ1c3QlfSZjbGllbnRJZD17bi5jbGllbnQuaWR9JnRzPXsldGltZXN0YW1wVSV9JnRzej17JXRpbWVzdGFtcFolfQ==", 
            "contenttype": "application/x-www-form-urlencoded",  
            "timeout": 4 
        }, 
        "showOffline": true, 
        "showRule": "always", 
        "endDate": 2524730400, 
        "startDate": 0, 
        "audiences": [], 
        "triggers": [ 
            { 
                "key": "pageName", 
                "matches": "eq", 
                "values": [ 
                    "MainMenu" 
                ] 
            } 
        ] 
    } 
] 
```

## Amostra de código {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

Como seu estado é `"MainMenu"`, essa chamada de rastreamento aciona a mensagem de postback acima. O URL substituirá todas as variáveis do modelo com valores da ocorrência. Supondo que a sessão anterior do usuário era de 132 segundos e que o usuário utiliza a versão 4.6.0 do Android SDK, o URL resultante seria como o seguinte:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
