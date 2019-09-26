---
description: É possível usar o SDK da Adobe para coletar informações de identificação pessoal (PII) e enviá-las para um terminal de terceiros.
seo-description: É possível usar o SDK da Adobe para coletar informações de identificação pessoal (PII) e enviá-las para um terminal de terceiros.
seo-title: Postbacks de PII
title: Postbacks de PII
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# PII postbacks {#pii-postbacks}

É possível usar o SDK da Adobe para coletar informações de identificação pessoal (PII) e enviá-las para um terminal de terceiros.

Quando quiser usar o SDK da Adobe para coletar PII, você deve enviar uma chamada de rastreamento de PII. Embora o uso desta chamada habilite a coleta de dados PII, o SDK não envia automaticamente os dados para nenhum terminal da Adobe. Um postback tipo PII precisa ser configurado no terminal apropriado.

>[!TIP]
>
>Um terminal compatível com HTTPS é necessário para usar o tipo de postback PII.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao seu projeto* em Implementação [principal e Ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe a biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Quando estiver pronto para capturar a PII, chame `trackPII` para enviar uma ocorrência para esta ação, evento ou exibição:

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```

