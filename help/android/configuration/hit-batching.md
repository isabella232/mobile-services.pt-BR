---
description: O agrupamento de ocorrências permite que aplicativos não as enviem até que o seu número na fila tenha excedido o limite configurado.
keywords: android;biblioteca;móvel;sdk
seo-description: O agrupamento de ocorrências permite que aplicativos não as enviem até que o seu número na fila tenha excedido o limite configurado.
seo-title: Agrupamento de ocorrências
solution: Experience Cloud,Analytics
title: Agrupamento de ocorrências
topic: Desenvolvedor e implementação
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Agrupamento de ocorrências {#hit-batching}

O agrupamento de ocorrências permite que aplicativos não as enviem até que o seu número na fila tenha excedido o limite configurado.

>[!IMPORTANT]
>
>Para usar o agrupamento de ocorrências, você **deve** habilitar o rastreamento offline e ter a versão 4.1 ou posterior do SDK

Para habilitar o agrupamento de ocorrências, atualize o arquivo `ADBMobileConfig.json` e especifique um valor para `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Quando o valor é configurado com um número maior que 0, o SDK enfileira o número de ocorrências igual ao valor *`batchLimit`*. Depois que esse limite é ultrapassado, todas as ocorrências na lista são enviadas.

Os métodos a seguir são usados com o agrupamento de ocorrências:

* `Analytics.getQueueSize` retorna `long` com o número de ocorrências atual na fila do agrupamento de ocorrências.

* `Analytics.sendQueuedHits` força a biblioteca a enviar todas as ocorrências na fila, independentemente de quantas estejam na fila no momento.
* `Analytics.clearQueue` limpa todas as ocorrências da fila sem enviá-las.
