---
description: É possível usar essas informações para ajudá-lo a entender os postbacks e como eles funcionam.
keywords: android;biblioteca;móvel;sdk
seo-description: É possível usar essas informações para ajudá-lo a entender os postbacks e como eles funcionam.
seo-title: Exemplo de postbacks
solution: Marketing Cloud,Analytics
title: Exemplo de postbacks
topic: Desenvolvedor e implementação
uuid: 8010cd00-d42b-4e16-8403-692fab2550f1
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postbacks example {#postbacks-example}

Você pode usar essas informações para ajudá-lo a entender o que são postbacks e como eles funcionam.

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

## Code sample {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. O URL substituirá todas as variáveis do modelo com valores da ocorrência. Supondo que a sessão anterior do usuário tenha sido de 132 segundos, e que o usuário esteja no Android SDK versão 4.6.0, o URL resultante terá a seguinte aparência:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
