---
description: Definição e exemplos de código-fonte para o recurso Postbacks.
seo-description: Definição e exemplos de código-fonte para o recurso Postbacks.
seo-title: Exemplo de postback
solution: Experience Cloud,Analytics
title: Exemplo de postback
topic: Desenvolvedor e implementação
uuid: 809c5646-7a80-40df-984b-0af89d854259
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Exemplo de postback {#postback-example}

Definição e exemplos de código-fonte para o recurso Postbacks.

>[!CAUTION]
>
>Este exemplo é fornecido apenas para fins informativos. O arquivo `ADBMobileConfig.json` deve ser configurado na interface do usuário do Adobe Mobile e não deve ser modificado manualmente. Um arquivo de configuração editado manualmente pode ser perigoso quando a configuração remota de mensagens estiver habilitada.

## Definição de ADBMobileConfig.json {#section_0F6EC001AB6D488E815F50C7F5DA022E}

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

## Amostra de código {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

Como seu estado é `“MainMenu”`, essa chamada de rastreamento aciona a mensagem de postback acima. O URL substituirá todas as variáveis do modelo com valores da ocorrência. Supondo que a sessão anterior do usuário tenha sido de 132 segundos e que o usuário esteja no iOS SDK versão 4.6.0, o URL resultante seria como o do exemplo seguinte:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`
