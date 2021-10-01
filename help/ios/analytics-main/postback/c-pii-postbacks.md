---
description: Você pode usar o SDK da Adobe para coletar informações de identificação pessoal (PII) e enviá-las para um endpoint de terceiros.
title: Postbacks de PII
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
exl-id: 180c21f7-0fba-4b9b-ab7f-7afe81b85f38
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 86%

---

# Postbacks de PII {#pii-postbacks}

Você pode usar o SDK da Adobe para coletar informações de identificação pessoal (PII) e enviá-las para um endpoint de terceiros.

Quando quiser usar o SDK da Adobe para coletar PII, você deve enviar uma chamada de rastreamento de PII. Embora o uso dessa chamada habilite a coleta de dados PII, o SDK não envia automaticamente os dados para nenhum endpoint do Adobe. Um postback tipo PII precisa ser configurado no terminal apropriado.

>[!TIP]
>
>Um terminal compatível com HTTPS é necessário para usar o tipo de postback PII.

## Rastreamento de postbacks de PII {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao seu projeto* em [Implementação principal e ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe a biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Quando estiver pronto para capturar a PII, chame `trackPII` para enviar uma ocorrência para esta ação, evento ou exibição:

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```
