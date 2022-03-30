---
description: As regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para eVars, props e outras variáveis para relatórios.
solution: Experience Cloud Services,Analytics
title: Regras de processamento e dados de contexto
topic-fix: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
exl-id: a3968160-42c4-4671-b541-c14639b8a451
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 67%

---

# Regras de processamento e dados de contexto {#processing-rules-and-context-data}

As regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para eVars, props e outras variáveis para relatórios.

Para obter mais informações sobre regras de processamento, consulte [Visão geral das regras de processamento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) na documentação do Adobe Analytics.

Ao trabalhar com as regras de processamento, lembre-se das seguintes informações:

* Agrupe as variáveis de dados de contexto usando o namespace para manter uma ordem lógica.

   Por exemplo, se você quiser coletar informações sobre um produto, defina as seguintes variáveis:

   ```js
   "product.type":"hat";
   "product.team":"mariners";
   "product.color":"blue";
   ```

* As variáveis de dados de contexto são classificadas alfabeticamente na interface de regras de processamento, o que permite que você veja rapidamente quais variáveis estão no mesmo namespace.

   Evite nomear chaves de dados de contexto usando o número do eVar ou da propriedade:

   ```js
   "eVar1":"jimbo";
   ```

   Isso pode tornar *um pouco* mais fácil ao executar o mapeamento único nas regras de processamento, mas você perde a legibilidade durante a depuração e futuras atualizações de código, o que pode ser mais difícil. Em vez disso, use nomes descritivos para chaves e valores:

   ```js
   "username":"jimbo";
   ```

* As variáveis de contexto que definem eventos de contador devem ser definidas como 1:

   ```js
   "logon":"1";
   ```

* Variáveis de dados de contexto que definem eventos incrementadores podem ter o evento como a chave e a quantidade que será incrementada como o valor:

   ```js
   "levels completed":"6";
   ```

>[!TIP]
>
>A Adobe reserva o namespace &quot; `a.`&quot;. Além dessa pequena restrição, para evitar colisões, o único requisito é que as variáveis de dados de contexto sejam únicas no logon da sua empresa.
