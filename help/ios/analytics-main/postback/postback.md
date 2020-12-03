---
description: Os postbacks permitem enviar dados coletados pelo SDK para um servidor de terceiros. Ao utilizar os mesmos disparadores e características usadas para exibir uma mensagem no aplicativo, é possível configurar o SDK para enviar dados personalizados a um destino de terceiros.
seo-description: Os postbacks permitem enviar dados coletados pelo SDK para um servidor de terceiros. Ao utilizar os mesmos disparadores e características usadas para exibir uma mensagem no aplicativo, é possível configurar o SDK para enviar dados personalizados a um destino de terceiros.
seo-title: Postbacks
solution: Experience Cloud,Analytics
title: Visão geral de postbacks
uuid: 25e2a5fb-1203-40dd-96cd-b23e0f23376d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 100%

---


# Visão geral dos postbacks {#postbacks}

Os postbacks permitem enviar dados coletados pelo SDK para um servidor de terceiros. Ao utilizar os mesmos disparadores e características usadas para exibir uma mensagem no aplicativo, é possível configurar o SDK para enviar dados personalizados a um destino de terceiros.

>[!IMPORTANT]
>
>Essa funcionalidade exige a versão 4.6.0 ou posterior do SDK.

As mensagens de postback são enfileiradas e seguem todas as regras online/offline existentes que regem a coleta de dados do Analytics. Quando uma mensagem corresponde (como as mensagens mostradas), as mensagens de postback não cancelam o restante das mensagens. Dessa forma, vários postbacks ocorram na mesma ocorrência de análise. Para obter a definição, consulte a linha *postbacks* em  [Configuração JSON do ADBMobile](/help/ios/configuration/json-config/json-config.md).

## Expansões do modelo {#section_6758AD05A24C4E9E965F5253294C164A}

Expansões do modelo estão disponíveis nas propriedades `templateurl` e `templatebody`. Os itens do modelo tomam a forma de `{key}`, em que `key` é uma chave de dados de contexto ou chave de dados tradicional. Os valores disponíveis para expansão do modelo são limitados à [lista de variáveis do ciclo de vida padrão](/help/ios/metrics.md), além de quaisquer dados personalizados anexados à ocorrência que aciona a mensagem. Nenhum dado baseado em histórico ou em segmento está disponível no momento.

Também há modelos específicos e reservados que o SDK substituirá automaticamente para você por dados internos conhecidos pelo SDK.

Esta lista inclui:

| Nome do token | Descrição do token |
|--- |--- |
| `{%sdkver%}` | Retorna a versão do SDK. |
| `{%cachebust%}` | Resolve um número aleatório entre 1 e 100000000. |
| `{%adid%}` | Retorna IDFA. Este token só funciona se você tiver usado `setAdvertisingIdentifier`. |
| `{%pushid%}` | Retorna o token do identificador de push. Este token só funciona se você tiver usado `setPushIdentifier`. |
| `{%timestampu%}` | Retorna o carimbo de data e hora atual em época. |
| `{%timestampz%}` | Retorna o carimbo de data e hora no formato JavaScript (ISO 8601). |