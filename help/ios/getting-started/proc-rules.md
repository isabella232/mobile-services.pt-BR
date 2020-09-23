---
description: 'As Regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para evars, props e outras variáveis de relatório. '
seo-description: 'As Regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para evars, props e outras variáveis de relatório. '
seo-title: Regras de processamento e dados de contexto
solution: Experience Cloud,Analytics
title: Regras de processamento e dados de contexto
topic: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 51%

---


# Regras de processamento e dados de contexto{#processing-rules-and-context-data}

As Regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para evars, props e outras variáveis de relatório. 

Para obter mais informações, consulte o seguinte conteúdo:

* [Treinamento](https://tv.adobe.com/embed/1181/16506/) das regras de processamento no Summit 2013
* Receber autorização para usar as regras de processamento

   Para obter mais informações sobre regras de processamento, consulte [Visão geral das regras de processamento](https://docs.adobe.com/content/help/pt-BR/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Ao trabalhar com as regras de processamento, lembre-se das seguintes informações:

* Agrupe suas variáveis de dados de contexto usando o namespace, pois isso ajuda a manter uma ordem lógica.

   Por exemplo, se você deseja coletar informações sobre um produto, pode definir as seguintes variáveis:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* As variáveis de dados de contexto são classificadas alfabeticamente na interface de regras de processamento, o que permite que você veja rapidamente quais variáveis estão na mesma namespace.

   Evite nomear chaves de dados de contexto usando o número de evar ou prop:

   ```js
   "eVar1":"jimbo"
   ```

   Isso pode tornar *um pouco* mais fácil ao executar o mapeamento único nas regras de processamento, mas você perde a legibilidade durante a depuração e futuras atualizações de código, o que pode ser mais difícil. Em vez disso, use nomes descritivos para chaves e valores:

   ```js
   "username":"jimbo"
   ```

* As variáveis de contexto que definem eventos de contador devem ser definidas como 1:

   ```js
   "logon":"1"
   ```

* As variáveis de dados de contexto que definem eventos de incremento podem ter o evento como a chave e o valor a incrementar como o valor:

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>A Adobe reserva o namespace &quot; `a.`&quot;. Além dessa pequena restrição, para evitar colisões, o único requisito é que as variáveis de dados de contexto sejam únicas no logon da sua empresa.

