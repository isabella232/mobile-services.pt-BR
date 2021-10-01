---
description: É possível carregar um arquivo de configuração JSON do ADBMobile diferente quando o aplicativo for iniciado.
solution: Experience Cloud,Analytics
title: Substituir o caminho de configuração JSON do ADBMobile
topic-fix: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
exl-id: 3a191e9c-905f-4bea-8a6f-5ccf5ea02aff
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 100%

---

# Substituir o caminho de configuração JSON do ADBMobile {#override-the-adbmobile-json-config-path}

É possível carregar um arquivo de configuração JSON do ADBMobile diferente quando o aplicativo for iniciado.

O método `ADBMobile overrideConfigPath:filePath` permite especificar o caminho para um arquivo de configuração `ADBMobile.json` diferente quando o aplicativo é iniciado. Esse método deve ser chamado no método `applicationDidFinishLaunchingWithOptions` e a chamada deve ocorrer antes de qualquer outra chamada do SDK da Experience Cloud, como `collectLifecycleData`.

Ao chamar esse método com um caminho diferente, ocorre uma substituição única do arquivo de configuração até que o aplicativo seja fechado.

Por exemplo:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```
