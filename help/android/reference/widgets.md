---
description: Os widgets do Android podem ser monitorados usando os mesmos métodos do seu aplicativo. Os widgets compartilham o contexto do aplicativo com o app, de forma que o pedido de ocorrência e a identificação de visitantes são preservados.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: Os widgets do Android podem ser monitorados usando os mesmos métodos do seu aplicativo. Os widgets compartilham o contexto do aplicativo com o app, de forma que o pedido de ocorrência e a identificação de visitantes são preservados.
seo-title: Widgets do Android
solution: Marketing Cloud, Analytics
title: Widgets do Android
topic: Desenvolvedor e implementação
uuid: 1 a 3718 ff -967 b -4 c 8 e-ae 0 b-ba 15 bddbda 0 a
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Android widgets {#android-widgets}

Os widgets do Android podem ser monitorados usando os mesmos métodos do seu aplicativo. Os widgets compartilham o contexto do aplicativo com o app, de forma que o pedido de ocorrência e a identificação de visitantes são preservados.

As diretrizes a seguir ajudarão você a monitorar os widgets do Android:

* Do not implement lifecycle metrics ( `startActivity`/ `stopActivity`) calls in the widget.

* Para monitorar quando um widget é adicionado à página inicial, adicione uma chamada `trackState` ou `trackEvent` ao método `onEnabled` do widget.

* Para monitorar quando o aplicativo é iniciado a partir de um widget, adicione uma chamada `trackState` ou `trackEvent` antes de iniciar o seu aplicativo.

* To track the context of an action, you can define a `ContextData` variable that provides the option to segment each action separately (for example, `AppExperienceType="widget"` vs. `app`).

