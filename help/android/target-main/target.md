---
description: É possível fornecer conteúdo direcionado nos aplicativos Android.
keywords: android;biblioteca;móvel;sdk
solution: Experience Cloud Services,Analytics
title: Configuração do Target
topic-fix: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
exl-id: dbcc3114-e76b-4b18-a418-ac46a21a593e
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '66'
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
