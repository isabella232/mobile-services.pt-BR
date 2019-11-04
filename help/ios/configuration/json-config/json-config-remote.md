---
description: É possível carregar um arquivo de configuração JSON do ADBMobile diferente quando o aplicativo for iniciado.
seo-description: É possível carregar um arquivo de configuração JSON do ADBMobile diferente quando o aplicativo for iniciado.
seo-title: Substituir o caminho de configuração JSON do ADBMobile
solution: Experience Cloud,Analytics
title: Substituir o caminho de configuração JSON do ADBMobile
topic: Desenvolvedor e implementação
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: ht
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

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

