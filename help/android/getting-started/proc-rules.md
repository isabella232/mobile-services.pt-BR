---
description: As Regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para evars, props e outras variáveis de relatório.
seo-description: As Regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para evars, props e outras variáveis de relatório.
seo-title: Regras de processamento e dados de contexto
solution: Marketing Cloud,Analytics
title: Regras de processamento e dados de contexto
topic: Desenvolvedor e implementação
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Processing rules and context data {#processing-rules-and-context-data}

As Regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para evars, props e outras variáveis de relatório. For more information, see Processing Rules.[](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

Ao trabalhar com regras de processamento, lembre-se das informações a seguir:

* Agrupe as variáveis de dados de contexto usando espaços para nome, isso ajudará a manter uma ordem lógica. Por exemplo, para coletar informações sobre um produto, é possível definir as variáveis a seguir:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* As variáveis de dados de contexto são classificadas em ordem alfabética na interface das regras de processamento, que permite visualizar rapidamente quais varáveis estão no mesmo espaço de nome.

   Evite nomear as chaves de dados de contexto usando número de evar ou de propriedade:

   ```js
   "eVar1":"jimbo"
   ```

   Isso pode fazer com que fique *um pouco* mais fácil completar o mapeamento esta única vez nas regras de processamento, mas você perde a legibilidade ao depurar atualizações de código futuras, o que acaba dificultando. Em vez disso, recomendamos que use nomes descritivos para chaves e valores:

   ```js
   "username":"jimbo"
   ```

* As variáveis de contexto que definem eventos de contagem devem ser definidas como 1:

   ```js
   "logon":"1"
   ```

* As variáveis de dados de contexto que definem os eventos de incremento podem ter o evento como a chave e o montante a incrementar como o valor:

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>A Adobe reserva o namespace `"a."`. Para evitar colisões, o único outro requisito é que as variáveis dos dados de contexto sejam únicas no logon da empresa.

