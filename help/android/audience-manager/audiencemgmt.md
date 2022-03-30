---
description: É possível enviar sinais e recuperar segmentos de visitantes no gerenciamento de público-alvo.
keywords: android;biblioteca;móvel;sdk
solution: Experience Cloud Services,Analytics
title: Configuração do Audience Manager
topic-fix: Developer and implementation
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
exl-id: 05033748-5461-482f-a01d-1ba73f64616a
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 100%

---

# Configuração do Audience Manager{#audience-manager-configuration}

É possível enviar sinais e recuperar segmentos de visitantes do Audience Manager.

## Definir o contexto do aplicativo {#section_37CAE496FF894FCA821F7760605574CA}

**(Obrigatório)** O método `setContext()` deve ser chamado uma vez no método `onCreate()` da atividade principal.

Esta é a amostra de código para este método:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Se você já adicionou esta chamada de método quando implementou o Analytics ou o Target, não é necessário adicioná-la novamente.
