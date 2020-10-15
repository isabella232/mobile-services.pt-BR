---
description: O agrupamento de ocorrências permite que aplicativos não as enviem até que o seu número na fila tenha excedido o limite configurado.
keywords: android;library;mobile;sdk
seo-description: O agrupamento de ocorrências permite que aplicativos não as enviem até que o seu número na fila tenha excedido o limite configurado.
seo-title: Agrupamento de ocorrências
solution: Experience Cloud,Analytics
title: Agrupamento de ocorrências
topic: Developer and implementation
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '183'
ht-degree: 100%

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

Quando o valor é configurado com um número maior que 0, o SDK enfileira o número de ocorrências igual ao valor *`batchLimit`*. Depois que esse limite for ultrapassado, todas as ocorrências na fila serão enviadas.

Os métodos a seguir são usados com o agrupamento de ocorrências:

* `Analytics.getQueueSize` retorna `long` com o número de ocorrências atual na fila do agrupamento de ocorrências.

* `Analytics.sendQueuedHits` força a biblioteca a enviar todas as ocorrências na fila, independentemente de quantas estejam na fila no momento.
* `Analytics.clearQueue` limpa todas as ocorrências da fila sem enviá-las.
