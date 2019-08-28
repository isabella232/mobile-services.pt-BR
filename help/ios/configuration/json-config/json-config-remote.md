---
description: É possível carregar um arquivo de configuração JSON do ADBMobile diferente ao iniciar o aplicativo.
seo-description: É possível carregar um arquivo de configuração JSON do ADBMobile diferente ao iniciar o aplicativo.
seo-title: Substituir o caminho de configuração JSON do adbmobile
solution: Marketing Cloud, Analytics
title: Substituir o caminho de configuração JSON do adbmobile
topic: Desenvolvedor e implementação
uuid: 0 d 1 be 674-c 634-4 a 48-aa 31-5701681911 b 9
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

É possível carregar um arquivo de configuração JSON do ADBMobile diferente ao iniciar o aplicativo.

`ADBMobile overrideConfigPath:filePath` O método permite especificar o caminho para um arquivo `ADBMobile.json` de configuração diferente quando o aplicativo é iniciado. Esse método deve ser chamado no método `applicationDidFinishLaunchingWithOptions` e a chamada deve ocorrer antes de qualquer outra chamada do SDK da Experience Cloud, como `collectLifecycleData`.

Quando você chama este método com um caminho diferente, uma substituição única do arquivo de configuração ocorre até que o aplicativo seja fechado.

Por exemplo:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

