---
description: O valor de vida útil permite medir e atribuir um valor para cada usuário Android. O valor pode ser usado para armazenar compras vitalícias, visualizações de anúncios, vídeos, compartilhamentos sociais, uploads de fotos etc.
seo-description: O valor de vida útil permite medir e atribuir um valor para cada usuário Android. O valor pode ser usado para armazenar compras vitalícias, visualizações de anúncios, vídeos, compartilhamentos sociais, uploads de fotos etc.
seo-title: Valor do tempo de vida do visitante
solution: Marketing Cloud, Analytics
title: Valor do tempo de vida do visitante
topic: Desenvolvedor e implementação
uuid: ba 0308 de -282 e -46 f 9-a 14 c -19 fb 6 d 5 c 363 e
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Visitor lifetime value {#visitor-lifetime-value}

O valor de vida útil permite medir e atribuir um valor para cada usuário Android. O valor pode ser usado para armazenar compras vitalícias, visualizações de anúncios, vídeos, compartilhamentos sociais, uploads de fotos etc.

Cada vez que um valor é enviado com `trackLifetimeValueIncrease`, o valor é adicionado ao valor existente. O valor de tempo de vida é armazenado no dispositivo e pode ser recuperado a qualquer momento ao chamar `lifetimeValue`.

## Track the visitor lifetime value {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Adicione a [biblioteca ao seu projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o Arquivo de configuração ao projeto intellij IDEA ou Eclipse* na [implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).
1. Importe a biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Chame `trackLifetimeValueIncrease` com o montante para aumentar o valor:

   ```java
   Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), null);
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Em adição ao valor da vida útil, é possível enviar dados de contexto adicionais com cada chamada de rastreamento de ação:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), cdata);
```

Os valores de dados de contexto devem ser mapeados para variáveis personalizadas nos Adobe Mobile Services:

![](assets/map-variable-context-ltv.png)

