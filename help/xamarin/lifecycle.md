---
description: Informações para ajudá-lo a implementar Medições de ciclo de vida para Android. As medições de ciclo de vida são coletadas automaticamente para iOS.
keywords: Xamarin
solution: Experience Cloud
title: Implementar o ciclo de vida
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
exl-id: c76e63d1-48a5-4831-85d5-f3d3e9798a43
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 7%

---

# Implementar o ciclo de vida {#implement-lifecycle}

Estas informações ajudam a implementar as Medições de ciclo de vida no Android.

>[!TIP]
>
>As medições de ciclo de vida são coletadas automaticamente para iOS.

Para as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel após a implementação do ciclo de vida, consulte [Medições de ciclo de vida](/help/ios/metrics.md).

## iOS

No iOS, as medições de ciclo de vida são coletadas automaticamente.

## Android

Na atividade principal, defina o contexto do aplicativo para o Android SDK.

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

Em cada atividade, implemente chamadas de ciclo de vida.

```java
protected override void OnResume()
{
    ...
    Config.CollectLifecycleData (this);
    ...
}
protected override void OnPause() 
{
    ...
    Config.PauseCollectingLifecycleData ();
    ...
}
```
