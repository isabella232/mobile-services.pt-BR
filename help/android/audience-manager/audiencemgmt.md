---
description: É possível enviar sinais e recuperar segmentos de visitantes no gerenciamento de público-alvo.
keywords: android;biblioteca;móvel;sdk
seo-description: É possível enviar sinais e recuperar segmentos de visitantes no gerenciamento de público-alvo.
seo-title: Configuração do Audience Manager
solution: Marketing Cloud,Analytics
title: Configuração do Audience Manager
topic: Desenvolvedor e implementação
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Audience Manager configuration{#audience-manager-configuration}

Você pode enviar sinais e recuperar segmentos de visitantes do Audience Manager.

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(Obrigatório)** O `setContext()` método deve ser chamado uma vez no `onCreate()` método da atividade principal.

Esta é a amostra de código para este método:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Se você tiver adicionado essa chamada de método ao implementar o Analytics ou o Target, não precisará adicioná-la novamente.
