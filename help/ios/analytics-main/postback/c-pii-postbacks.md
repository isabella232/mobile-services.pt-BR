---
description: É possível usar o SDK da Adobe para coletar informações de identificação pessoal (PII) e enviá-las para um terminal de terceiros.
seo-description: É possível usar o SDK da Adobe para coletar informações de identificação pessoal (PII) e enviá-las para um terminal de terceiros.
seo-title: Postbacks de PII
title: Postbacks de PII
uuid: 08 f 76 a 52-75 dd -4 fc 1-b 4 cc -4 f 5 eef 93 d 0 f 7
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# PII postbacks {#pii-postbacks}

É possível usar o SDK da Adobe para coletar informações de identificação pessoal (PII) e enviá-las para um terminal de terceiros.

Quando quiser usar o SDK da Adobe para coletar PII, você deve enviar uma chamada de rastreamento de PII. Embora o uso desta chamada habilite a coleta de dados PII, o SDK não envia automaticamente os dados para nenhum terminal da Adobe. Um postback tipo PII precisa ser configurado no terminal apropriado.

>[!TIP]
>
>É necessário um terminal compatível com HTTPS para usar o tipo de postback PII.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o Arquivo de configuração ao projeto* na [Implementação principal e no ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe a biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Quando estiver pronto para capturar a PII, chame `trackPII` para enviar uma ocorrência para esta ação, evento ou exibição:

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```

