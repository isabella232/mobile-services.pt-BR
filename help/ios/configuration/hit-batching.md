---
description: O agrupamento de ocorrências permite que os aplicativos com rastreamento offline habilitado não as enviem até que o seu número na fila passe do limite configurável.
solution: Experience Cloud Services,Analytics
title: Agrupamento de ocorrências
topic-fix: Developer and implementation
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
exl-id: af21f435-13cb-4353-9fbb-c99274bce411
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 100%

---

# Agrupamento de ocorrências {#hit-batching}

O agrupamento de ocorrências permite que os aplicativos com rastreamento offline habilitado não as enviem até que o seu número na fila passe do limite configurável.

>[!IMPORTANT]
>
>O agrupamento de ocorrências exige a versão 4.1 ou posterior do SDK.

Para habilitar o agrupamento de ocorrências, atualize o arquivo `ADBMobileConfig.json` e especifique um valor para `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Quando configurado para um número superior a 0, o SDK enfileira o número de ocorrências igual a *`batchLimit`*. Depois que esse limite for ultrapassado, todas as ocorrências na fila serão enviadas.

Os métodos a seguir são usados com o agrupamento de ocorrências:

* `trackingGetQueueSize()` retorna um `NSUInteger` com o número de ocorrências na fila de agrupamento.
* `trackingSendQueuedHits()` força a biblioteca a enviar todas as ocorrências na fila, independentemente de quantas estão na fila no momento.
* `trackingClearQueue()` limpa todas as ocorrências da fila sem enviá-las.

>[!CAUTION]
>
>O rastreamento offline deve ser habilitado para usar o agrupamento de ocorrências.
