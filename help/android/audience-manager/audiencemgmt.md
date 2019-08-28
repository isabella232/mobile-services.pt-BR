---
description: É possível enviar sinais e recuperar segmentos de visitantes no gerenciamento de público-alvo.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: É possível enviar sinais e recuperar segmentos de visitantes no gerenciamento de público-alvo.
seo-title: Configuração do Audience Manager
solution: Marketing Cloud, Analytics
title: Configuração do Audience Manager
topic: Desenvolvedor e implementação
uuid: f 68 d 5 b 2 e-fa 2 c -4 db 6-98 ad-d 1855 a 2 c 45 ac
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Audience Manager configuration{#audience-manager-configuration}

É possível enviar sinais e recuperar segmentos de visitantes do Audience Manager.

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

Se você adicionou essa chamada de método quando implementou o Analytics ou o Target, não é necessário adicioná-la novamente.
