---
description: As Regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para evars, props e outras variáveis de relatório.
seo-description: As Regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para evars, props e outras variáveis de relatório.
seo-title: Regras de processamento e dados de contexto
solution: Marketing Cloud, Analytics
title: Regras de processamento e dados de contexto
topic: Desenvolvedor e implementação
uuid: 51338 ccd-fa 52-4 d 9 c -97 c 4-947 a 4100465 d
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Processing rules and context data{#processing-rules-and-context-data}

As Regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para evars, props e outras variáveis de relatório.

Para obter mais informações, consulte o seguinte conteúdo:

* [Treinamento sobre regras de processamento](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013
* Receber autorização para usar regras de processamento

   Para obter mais informações sobre regras de processamento, consulte [Visão geral das regras de processamento](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Ao trabalhar com as regras de processamento, lembre-se das seguintes informações:

* Agrupe as variáveis de dados de contexto usando espaços para nome, isso ajudará a manter uma ordem lógica.

   Por exemplo, se você quiser coletar informações sobre um produto, pode definir as seguintes variáveis:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* As variáveis de dados de contexto são classificadas em ordem alfabética na interface de regras de processamento, o que permite ver rapidamente quais variáveis estão no mesmo espaço de nome.

   Evite nomear as chaves de dados de contexto usando número de evar ou de propriedade:

   ```js
   "eVar1":"jimbo"
   ```

   Isso pode facilitar *um pouco* a execução do mapeamento único nas regras de processamento, mas você perderá a legibilidade durante a depuração e futuras atualizações de código, o que pode ser mais difícil. Em vez disso, use nomes descritivos nas chaves e nos valores:

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
>A Adobe reserva o namespace " `a.`". Além dessa pequena restrição, para evitar colisões, o único requisito é que as variáveis de dados de contexto sejam únicas no logon da sua empresa.

