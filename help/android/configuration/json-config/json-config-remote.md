---
description: É possível carregar um arquivo de configuração JSON do ADBMobile diferente quando o aplicativo é iniciado.
seo-description: É possível carregar um arquivo de configuração JSON do ADBMobile diferente quando o aplicativo é iniciado.
seo-title: Substituir o caminho de configuração ADBMobile JSON
solution: Marketing Cloud, Analytics
title: Substituir o caminho de configuração ADBMobile JSON
topic: Desenvolvedor e implementação
uuid: 6872 a 5 d 7-0 c 5 a -4 fdc-b 7 bf-ad 1534763 a 6 a
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

É possível carregar um arquivo de configuração JSON do ADBMobile diferente quando o aplicativo é iniciado.

`Config.overrideConfigStream(configInput)` O método permite especificar o caminho para um arquivo `ADBMobile.json` de configuração diferente quando o aplicativo é iniciado. This method must be called before any other Experience Cloud SDK call (before `Config.collectLifecycleData()` ), typically in the `onCreate` method of your first loaded activity.

Chamar esse método com um caminho diferente causa uma substituição única do arquivo de configuração até que o aplicativo seja fechado.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```

