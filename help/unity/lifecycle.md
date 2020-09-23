---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Implementar o ciclo de vida
solution: Experience Cloud
title: Implementar o ciclo de vida
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 11%

---


# Implementar o ciclo de vida{#implement-lifecycle}

Para obter mais informações sobre as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel após a implementação do ciclo de vida, consulte Medições de [ciclo de vida no Android](/help/android/metrics.md) ou [Ciclo de vida no iOS](/help/ios/metrics.md).

## iOS

As medições de ciclo de vida são coletadas automaticamente no iOS.

## Android

No script do Unity, você define o contexto do aplicativo para o Android SDK. Adicione o seguinte código à `Awake()` função da PRIMEIRA cena:

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

Para coletar medições de ciclo de vida, adicione o seguinte código a todos os scripts de cena:

```java
void OnEnable()
 {
  ...
  ADBMobile.CollectLifecycleData (); 
  ...
 }
 
 void OnDisable()
 {
  ...
  ADBMobile.PauseCollectingLifecycleData (); 
  ...
 }
  
 void OnApplicationPause(bool isPaused) 
 {
  ...
  if (isPaused) {
   ADBMobile.PauseCollectingLifecycleData (); 
  }  
  else {
   ADBMobile.CollectLifecycleData(); 
  }
  ...
 }
```

