---
description: O agrupamento de ocorrências permite que aplicativos não as enviem até que o seu número na fila tenha excedido o limite configurado.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: O agrupamento de ocorrências permite que aplicativos não as enviem até que o seu número na fila tenha excedido o limite configurado.
seo-title: Agrupamento de ocorrência
solution: Marketing Cloud, Analytics
title: Agrupamento de ocorrência
topic: Desenvolvedor e implementação
uuid: ada 35 be 3-242 b -4 b 2 b-a 828-9 bf 998 dd 58 b 5
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Agrupamento de hits {#hit-batching}

O agrupamento de ocorrências permite que aplicativos não as enviem até que o seu número na fila tenha excedido o limite configurado.

>[!IMPORTANT]
>
>Para usar o agrupamento de ocorrências, você **deve** ativar o rastreamento offline e ter o SDK versão 4.1 ou posterior

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

When the value is set to a number greater than 0, the SDK queues the number of hits equal to the *`batchLimit`* value. Depois que esse limite é ultrapassado, todas as ocorrências na lista são enviadas.

Os métodos a seguir são usados com o agrupamento de ocorrência:

* `Analytics.getQueueSize` retorna `long` com o número de ocorrências atualmente na fila do agrupamento de ocorrência.

* `Analytics.sendQueuedHits` força a biblioteca a enviar todas as ocorrências na fila, independentemente de quantas estejam na fila no momento.
* `Analytics.clearQueue` limpa todas as ocorrências da fila sem enviá-las.
