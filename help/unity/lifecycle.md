---
description: Meça métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel
keywords: Unity
solution: Experience Cloud
title: Implementar o ciclo de vida
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 7%

---

# Implementar o ciclo de vida{#implement-lifecycle}

Para obter mais informações sobre as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel após a implementação do ciclo de vida, consulte [Medições de ciclo de vida no Android](/help/android/metrics.md) ou [Ciclo de vida no iOS](/help/ios/metrics.md).

## iOS

As medições de ciclo de vida são coletadas automaticamente no iOS.

## Android

No script do Unity, você define o contexto do aplicativo para o Android SDK. Adicione o seguinte código à função `Awake()` da PRIMEIRA cena:

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
