---
description: O valor vitalício permite medir e definir como meta um valor da vida útil para cada usuário do Android. O valor pode ser usado para armazenar compras vitalícias, visualizações de anúncios, conclusões de vídeo, compartilhamentos sociais, uploads de fotos e assim por diante.
solution: Experience Cloud,Analytics
title: Valor vitalício do visitante
topic-fix: Developer and implementation
uuid: ba0308de-282e-46f9-a14c-19fb6d5c363e
exl-id: 93c6d711-c7c0-4fca-93b2-6a6fc19377bd
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 100%

---

# Valor vitalício do visitante {#visitor-lifetime-value}

O valor vitalício permite medir e definir como meta um valor da vida útil para cada usuário do Android. O valor pode ser usado para armazenar compras vitalícias, visualizações de anúncios, conclusões de vídeo, compartilhamentos sociais, uploads de fotos e assim por diante.

Cada vez que um valor é enviado com `trackLifetimeValueIncrease`, o valor é adicionado ao valor existente. O valor de tempo de vida é armazenado no dispositivo e pode ser recuperado a qualquer momento ao chamar `lifetimeValue`.

## Rastrear o valor vitalício do visitante {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto IntelliJ IDEA ou Eclipse* na [Implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).
1. Importe a biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Chame `trackLifetimeValueIncrease` com o montante para aumentar o valor:

   ```java
   Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), null);
   ```

## Enviar dados adicionais {#section_3EBE813E54A24F6FB669B2478B5661F9}

Em adição ao valor da vida útil, é possível enviar dados de contexto adicionais com cada chamada de rastreamento de ação:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), cdata);
```

Os valores de dados de contexto devem ser mapeados para variáveis personalizadas nos Adobe Mobile Services:

![](assets/map-variable-context-ltv.png)
