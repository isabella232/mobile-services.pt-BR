---
description: Você pode usar o SDK do Adobe para coletar informações de identificação pessoal (PII) e enviá-las para um terminal de terceiros.
seo-description: Você pode usar o SDK do Adobe para coletar informações de identificação pessoal (PII) e enviá-las para um terminal de terceiros.
seo-title: Postbacks de PII
title: Postbacks de PII
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 47%

---


# Postbacks de PII {#pii-postbacks}

Você pode usar o SDK do Adobe para coletar informações de identificação pessoal (PII) e enviá-las para um terminal de terceiros.

Quando quiser usar o SDK Adobe para coletar PII, você deve enviar uma chamada de rastreamento PII. Embora o uso dessa chamada habilite a coleta de dados de PII, o SDK não envia automaticamente os dados para um terminal Adobe. Um postback tipo PII precisa ser configurado no terminal apropriado.

>[!TIP]
>
>Um terminal compatível com HTTPS é necessário para usar o tipo de postback PII.

## Rastreamento de postbacks de PII {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto IntelliJ IDEA ou Eclipse* na [Implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Importe a biblioteca:

   ```java
   #import "ADBMobile.h"
   ```

1. Quando estiver pronto para capturar a PII, chame `trackPII` para enviar uma ocorrência para esta ação, evento ou exibição:

   ```java
   Config.collectPII(new HashMap<String, Object>(){{
     put("key","value");
   }});
   ```

