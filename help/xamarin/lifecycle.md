---
description: Informações para ajudá-lo a implementar Medições de ciclo de vida para Android. Medições de ciclo de vida são automaticamente coletadas para iOS.
keywords: Xamarin
seo-description: Informações para ajudá-lo a implementar Medições de ciclo de vida para Android. Medições de ciclo de vida são automaticamente coletadas para iOS.
seo-title: Implementar o ciclo de vida
solution: Marketing Cloud,Desenvolvedor
title: Implementar o ciclo de vida
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implement lifecycle {#implement-lifecycle}

Essas informações ajudam a implementar medições de ciclo de vida para Android.

>[!TIP]
>
>Medições de ciclo de vida são automaticamente coletadas para iOS.

For the metrics and dimensions that can be measured automatically by the mobile library after lifecycle is implemented, see [Lifecycle Metrics](/help/ios/metrics.md).

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
