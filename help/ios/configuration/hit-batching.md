---
description: O agrupamento de ocorrências permite que os aplicativos com rastreamento offline habilitado não as enviem até que o seu número na fila passe do limite configurável.
seo-description: O agrupamento de ocorrências permite que os aplicativos com rastreamento offline habilitado não as enviem até que o seu número na fila passe do limite configurável.
seo-title: Hit batching
solution: Marketing Cloud,Analytics
title: Hit batching
topic: Desenvolvedor e implementação
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Agrupamento de hits {#hit-batching}

O agrupamento de ocorrências permite que os aplicativos com rastreamento offline habilitado não as enviem até que o seu número na fila passe do limite configurável.

>[!IMPORTANT]
>
>O agrupamento de ocorrências requer o SDK versão 4.1 ou posterior.

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Quando configurado para um número superior a 0, o SDK enfileira o número de ocorrências igual a *`batchLimit`*. Depois que esse limite é ultrapassado, todas as ocorrências na lista são enviadas.

Os métodos a seguir são usados com o agrupamento de ocorrência:

* `trackingGetQueueSize()` retorna um `NSUInteger` com o número de ocorrências na fila de agrupamento.
* `trackingSendQueuedHits()` força a biblioteca a enviar todas as ocorrências na fila, independentemente de quantas estão na fila no momento.
* `trackingClearQueue()` limpa todas as ocorrências da fila sem enviá-las.

>[!CAUTION]
>
>O rastreamento offline deve ser habilitado para usar o agrupamento de ocorrências.

