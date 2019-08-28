---
description: É possível fornecer conteúdo direcionado nos aplicativos Android.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: É possível fornecer conteúdo direcionado nos aplicativos Android.
seo-title: Configuração do Target
solution: Marketing Cloud, Analytics
title: Configuração do Target
topic: Desenvolvedor e implementação
uuid: 09 fe 2 c 9 c -7 b 60-49 c 3-bb 9 d -36 a 30 ce 7 c 350
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Target configuration {#target-configuration}

É possível fornecer conteúdo direcionado nos aplicativos Android.

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(Obrigatório)** O `setContext()` método deve ser chamado uma vez no `onCreate()` método da atividade principal.

Por exemplo:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Se já tiver adicionada esta chamada de método ao implementar o Analytics ou o Gerenciamento de público-alvo, não é necessário adicioná-la novamente.
