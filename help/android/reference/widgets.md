---
description: Os dispositivos do Android podem ser rastreados usando os mesmos métodos do seu aplicativo. Os dispositivos compartilham o contexto do aplicativo com seu aplicativo, portanto a ordem de ocorrência e a identificação do visitante são preservadas.
keywords: android;library;mobile;sdk
seo-description: Os dispositivos do Android podem ser rastreados usando os mesmos métodos do seu aplicativo. Os dispositivos compartilham o contexto do aplicativo com seu aplicativo, portanto a ordem de ocorrência e a identificação do visitante são preservadas.
seo-title: Dispositivos do Android
solution: Experience Cloud,Analytics
title: Dispositivos do Android
topic: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '179'
ht-degree: 100%

---


# Dispositivos do Android {#android-widgets}

Os dispositivos do Android podem ser rastreados usando os mesmos métodos do seu aplicativo. Os dispositivos compartilham o contexto do aplicativo com seu aplicativo, portanto a ordem de ocorrência e a identificação do visitante são preservadas.

As diretrizes a seguir ajudarão você a rastrear os dispositivos do Android:

* Não implemente chamadas de métricas de ciclo de vida (`startActivity`/ `stopActivity`) no dispositivo.

* Para monitorar quando um widget é adicionado à página inicial, adicione uma chamada `trackState` ou `trackEvent` ao método `onEnabled` do widget.

* Para monitorar quando o aplicativo é iniciado a partir de um widget, adicione uma chamada `trackState` ou `trackEvent` antes de iniciar o seu aplicativo.

* Para monitorar o contexto de uma ação, é possível definir uma variável `ContextData` que forneça a opção para segmentar cada ação separadamente (por exemplo, `AppExperienceType="widget"` versus `app`).

