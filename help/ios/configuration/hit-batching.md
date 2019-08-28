---
description: O agrupamento de ocorrências permite que os aplicativos com rastreamento offline habilitado não as enviem até que o seu número na fila passe do limite configurável.
seo-description: O agrupamento de ocorrências permite que os aplicativos com rastreamento offline habilitado não as enviem até que o seu número na fila passe do limite configurável.
seo-title: Hit batching
solution: Marketing Cloud, Analytics
title: Hit batching
topic: Desenvolvedor e implementação
uuid: 3 dda 7372-0695-4 cb 7-b 779-6 abca 2 d 6 e 0 d 9
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Agrupamento de hits {#hit-batching}

O agrupamento de ocorrências permite que os aplicativos com rastreamento offline habilitado não as enviem até que o seu número na fila passe do limite configurável.

>[!IMPORTANT]
>
>O agrupamento de ocorrências exige a versão 4.1 ou posterior do SDK.

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

