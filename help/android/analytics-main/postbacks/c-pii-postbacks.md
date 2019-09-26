---
description: É possível usar o SDK da Adobe para coletar informações de identificação pessoal (PII) e enviá-las para um terminal de terceiros.
seo-description: É possível usar o SDK da Adobe para coletar informações de identificação pessoal (PII) e enviá-las para um terminal de terceiros.
seo-title: Postbacks de PII
title: Postbacks de PII
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
translation-type: tm+mt
source-git-commit: 70ac08c74e11a68d94d3f10ed6d7fc133d34149d

---


# PII postbacks {#pii-postbacks}

É possível usar o SDK da Adobe para coletar informações de identificação pessoal (PII) e enviá-las para um terminal de terceiros.

Quando quiser usar o SDK da Adobe para coletar PII, você deve enviar uma chamada de rastreamento de PII. Embora o uso desta chamada habilite a coleta de dados PII, o SDK não envia automaticamente os dados para nenhum terminal da Adobe. Um postback tipo PII precisa ser configurado no terminal apropriado.

>[!TIP]
>
>Um terminal compatível com HTTPS é necessário para usar o tipo de postback PII.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Adicione [a biblioteca ao seu projeto e implemente o ciclo de vida.

   For more information, see Add the SDK and Config File to your IntelliJ IDEA or Eclipse Project in Core implementation and lifecycle.**[](/help/android/getting-started/dev-qs.md)

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

