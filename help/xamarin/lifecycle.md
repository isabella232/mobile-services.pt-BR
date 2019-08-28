---
description: Informações para ajudá-lo a implementar Medições de ciclo de vida para Android. Medições de ciclo de vida são automaticamente coletadas para iOS.
keywords: Xamarin
seo-description: Informações para ajudá-lo a implementar Medições de ciclo de vida para Android. Medições de ciclo de vida são automaticamente coletadas para iOS.
seo-title: Implementar ciclo de vida
solution: Marketing Cloud, desenvolvedor
title: Implementar ciclo de vida
uuid: 6 dccc 12 e -8 b 57-4231-9 c 74-d 47 bc 0 ac 93 ba
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implement lifecycle {#implement-lifecycle}

Estas informações ajudam a implementar medições de ciclo de vida para Android.

>[!TIP]
>
>Medições de ciclo de vida são automaticamente coletadas para iOS.

For the metrics and dimensions that can be measured automatically by the mobile library after lifecycle is implemented, see [Lifecycle Metrics](/help/ios/metrics.md).

## iOS

No iOS, as medições de ciclo de vida são coletadas automaticamente.

## Android

Na atividade principal, defina o contexto do aplicativo para o SDK do Android.

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

Em todas as atividades, implemente chamadas de ciclo de vida.

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
