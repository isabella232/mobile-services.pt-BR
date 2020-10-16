---
description: É possível fornecer conteúdo direcionado nos aplicativos Android.
keywords: android;library;mobile;sdk
seo-description: É possível fornecer conteúdo direcionado nos aplicativos Android.
seo-title: Configuração do Target
solution: Experience Cloud,Analytics
title: Configuração do Target
topic: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '72'
ht-degree: 100%

---


# Configuração do Target {#target-configuration}

É possível fornecer conteúdo direcionado nos aplicativos Android.

## Definir o contexto do aplicativo {#section_37CAE496FF894FCA821F7760605574CA}

**(Obrigatório)** O método `setContext()` deve ser chamado uma vez no método `onCreate()` da atividade principal.

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
