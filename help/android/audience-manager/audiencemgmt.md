---
description: É possível enviar sinais e recuperar segmentos de visitantes no gerenciamento de público-alvo.
keywords: android;library;mobile;sdk
seo-description: É possível enviar sinais e recuperar segmentos de visitantes no gerenciamento de público-alvo.
seo-title: Configuração do Audience Manager
solution: Experience Cloud,Analytics
title: Configuração do Audience Manager
topic: Developer and implementation
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 100%

---


# Configuração do Audience Manager {#audience-manager-configuration}

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
