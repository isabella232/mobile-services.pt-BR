---
description: As regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para eVars, props e outras variáveis para relatórios.
solution: Experience Cloud,Analytics
title: Regras de processamento e dados de contexto
topic-fix: Developer and implementation
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
exl-id: 543201fd-8118-485f-8235-26ec8f9bbb11
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 72%

---

# Regras de processamento e dados de contexto  {#processing-rules-and-context-data}

As regras de processamento são usadas para copiar os dados enviados em variáveis de dados de contexto para eVars, props e outras variáveis para relatórios. Para obter mais informações, consulte [Regras de processamento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Ao trabalhar com as regras de processamento, lembre-se das seguintes informações:

* Agrupe as variáveis de dados de contexto usando o namespace para manter uma ordem lógica. Por exemplo, para coletar informações sobre um produto, você pode definir as seguintes variáveis:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* As variáveis de dados de contexto são classificadas alfabeticamente na interface de regras de processamento, o que permite que você veja rapidamente quais variáveis estão no mesmo namespace.

   Evite nomear chaves de dados de contexto usando o número do eVar ou da propriedade:

   ```js
   "eVar1":"jimbo"
   ```

   Isso pode tornar *um pouco* mais fácil ao concluir o mapeamento único nas regras de processamento, mas você perde a legibilidade durante a depuração e futuras atualizações de código, o que pode ser mais difícil. Em vez disso, recomendamos usar nomes descritivos para chaves e valores:

   ```js
   "username":"jimbo"
   ```

* As variáveis de contexto que definem eventos de contador devem ser definidas como 1:

   ```js
   "logon":"1"
   ```

* Variáveis de dados de contexto que definem eventos incrementadores podem ter o evento como a chave e a quantidade que será incrementada como o valor:

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>A Adobe reserva o namespace `"a."`. Para evitar colisões, o único outro requisito é que as variáveis dos dados de contexto sejam únicas no logon da empresa.
