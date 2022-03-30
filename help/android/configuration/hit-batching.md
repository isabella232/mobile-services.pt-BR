---
description: O agrupamento de ocorrências permite que aplicativos não as enviem até que o seu número na fila tenha excedido o limite configurado.
keywords: android;biblioteca;móvel;sdk
solution: Experience Cloud Services,Analytics
title: Agrupamento de ocorrências
topic-fix: Developer and implementation
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
exl-id: 74147f09-52fc-46dc-b4dd-2bf60b039f6e
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '162'
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
