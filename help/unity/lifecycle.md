---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Implementação do ciclo de vida
solution: Marketing Cloud, desenvolvedor
title: Implementação do ciclo de vida
uuid: 7 ff 2 c 194-569 c -42 a 6-922 d-dccd 2 aa 9 eb 8 d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implementação do ciclo de vida{#implement-lifecycle}

Para obter mais informações sobre as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel depois que o ciclo de vida é implementado, consulte [Medições de ciclo de vida no Android](/help/android/metrics.md) ou [Lifecycle no iOS](/help/ios/metrics.md).

## iOS

As medições de ciclo de vida são coletadas automaticamente no iOS.

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

