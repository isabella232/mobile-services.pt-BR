---
description: É possível carregar um arquivo de configuração JSON do ADBMobile diferente ao iniciar o aplicativo.
seo-description: É possível carregar um arquivo de configuração JSON do ADBMobile diferente ao iniciar o aplicativo.
seo-title: Substituir o caminho de configuração ADBMobile JSON
solution: Marketing Cloud,Analytics
title: Substituir o caminho de configuração ADBMobile JSON
topic: Desenvolvedor e implementação
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

É possível carregar um arquivo de configuração JSON do ADBMobile diferente ao iniciar o aplicativo.

The `ADBMobile overrideConfigPath:filePath` method allows you to specify the path to a different `ADBMobile.json` configuration file when the application starts. Esse método deve ser chamado no método `applicationDidFinishLaunchingWithOptions` e a chamada deve ocorrer antes de qualquer outra chamada do SDK da Experience Cloud, como `collectLifecycleData`.

Quando você chama esse método com um caminho diferente, uma substituição única do arquivo de configuração ocorre até que o aplicativo seja fechado.

Por exemplo:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

