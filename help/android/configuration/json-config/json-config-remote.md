---
description: É possível carregar um arquivo de configuração JSON do ADBMobile diferente quando o aplicativo é iniciado.
seo-description: É possível carregar um arquivo de configuração JSON do ADBMobile diferente quando o aplicativo é iniciado.
seo-title: Substituir o caminho de configuração JSON do ADBMobile
solution: Experience Cloud,Analytics
title: Substituir o caminho de configuração JSON do ADBMobile
topic: Desenvolvedor e implementação
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Substituir o caminho de configuração JSON do ADBMobile {#override-the-adbmobile-json-config-path}

É possível carregar um arquivo de configuração JSON do ADBMobile diferente quando o aplicativo é iniciado.

O método `Config.overrideConfigStream(configInput)` permite especificar o caminho para um arquivo de configuração `ADBMobile.json` diferente quando o aplicativo é iniciado. Este método deve ser chamado antes de qualquer chamada de SDK da Experience Cloud (antes de `Config.collectLifecycleData()` ), normalmente no método `onCreate` da primeira atividade carregada.

Chamar esse método com um caminho diferente causa uma substituição única do arquivo de configuração até que o aplicativo seja fechado.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```

