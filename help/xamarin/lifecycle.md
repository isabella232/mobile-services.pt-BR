---
description: Informações para ajudá-lo a implementar Medições de ciclo de vida para Android. As medições de ciclo de vida são coletadas automaticamente para iOS.
keywords: Xamarin
seo-description: Informações para ajudá-lo a implementar Medições de ciclo de vida para Android. As medições de ciclo de vida são coletadas automaticamente para iOS.
seo-title: Implementar o ciclo de vida
solution: Experience Cloud
title: Implementar o ciclo de vida
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 7%

---


# Implementar o ciclo de vida {#implement-lifecycle}

Essas informações ajudam a implementar medições de ciclo de vida para Android.

>[!TIP]
>
>As medições de ciclo de vida são coletadas automaticamente para iOS.

Para as métricas e dimensões que podem ser medidas automaticamente pela biblioteca móvel após a implementação do ciclo de vida, consulte Medições [de ciclo de vida](/help/ios/metrics.md).

## iOS

No iOS, as medições de ciclo de vida são coletadas automaticamente.

## Android

Na sua atividade principal, defina o contexto do aplicativo para o Android SDK.

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
