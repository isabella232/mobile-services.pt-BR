---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Implementação do ciclo de vida
solution: Marketing Cloud,Developer
title: Implementação do ciclo de vida
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implementação do ciclo de vida{#implement-lifecycle}

Para obter mais informações sobre as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel após a implementação do ciclo de vida, consulte Medições de [ciclo de vida no Android](/help/android/metrics.md) ou [Ciclo de vida no iOS](/help/ios/metrics.md).

## iOS

Lifecycle metrics are automatically collected in iOS.

## Android

No script do Unity, você define o contexto do aplicativo para o SDK do Android. Add the following code to the `Awake()` function of your FIRST scene:

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

Para coletar métricas de ciclo de vida, adicione o seguinte código a todos os scripts da cena:

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

