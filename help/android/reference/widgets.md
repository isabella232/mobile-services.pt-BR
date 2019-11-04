---
description: Os widgets do Android podem ser monitorados usando os mesmos métodos do seu aplicativo. Os widgets compartilham o contexto do aplicativo com o app, de forma que o pedido de ocorrência e a identificação de visitantes são preservados.
keywords: android;biblioteca;móvel;sdk
seo-description: Os widgets do Android podem ser monitorados usando os mesmos métodos do seu aplicativo. Os widgets compartilham o contexto do aplicativo com o app, de forma que o pedido de ocorrência e a identificação de visitantes são preservados.
seo-title: Widgets do Android
solution: Experience Cloud,Analytics
title: Widgets do Android
topic: Desenvolvedor e implementação
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Widgets do Android {#android-widgets}

Os widgets do Android podem ser monitorados usando os mesmos métodos do seu aplicativo. Os widgets compartilham o contexto do aplicativo com o app, de forma que o pedido de ocorrência e a identificação de visitantes são preservados.

As diretrizes a seguir ajudarão você a monitorar os widgets do Android:

* Não implemente chamadas de métricas de ciclo de vida (`startActivity`/ `stopActivity`) no widget.

* Para monitorar quando um widget é adicionado à página inicial, adicione uma chamada `trackState` ou `trackEvent` ao método `onEnabled` do widget.

* Para monitorar quando o aplicativo é iniciado a partir de um widget, adicione uma chamada `trackState` ou `trackEvent` antes de iniciar o seu aplicativo.

* Para monitorar o contexto de uma ação, é possível definir uma variável `ContextData` que forneça a opção para segmentar cada ação separadamente (por exemplo, `AppExperienceType="widget"` versus `app`).

