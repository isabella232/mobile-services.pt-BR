---
description: Os postbacks permitem enviar dados coletados pelo SDK para um servidor de terceiros. Ao utilizar os mesmos disparadores e características usadas para exibir uma mensagem no aplicativo, é possível configurar o SDK para enviar dados personalizados a um destino de terceiros.
keywords: android;library;mobile;sdk
seo-description: Os postbacks permitem enviar dados coletados pelo SDK para um servidor de terceiros. Ao utilizar os mesmos disparadores e características usadas para exibir uma mensagem no aplicativo, é possível configurar o SDK para enviar dados personalizados a um destino de terceiros.
seo-title: Postbacks
solution: Experience Cloud,Analytics
title: Visão geral de postbacks
topic: Developer and implementation
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '349'
ht-degree: 100%

---


# Postbacks {#postbacks}

Os postbacks permitem enviar dados coletados pelo SDK para um servidor de terceiros. Ao utilizar os mesmos disparadores e características usadas para exibir uma mensagem no aplicativo, é possível configurar o SDK para enviar dados personalizados a um destino de terceiros.

>[!IMPORTANT]
>
>Essa funcionalidade exige a versão 4.6.0 ou posterior do SDK.

As mensagens de postback são enfileiradas e seguem todas as regras online/offline existentes que regem a coleta de dados do Analytics. Quando uma mensagem corresponde (como as mensagens mostradas), as mensagens de postback não cancelam o restante das mensagens. Dessa forma, vários postbacks ocorram na mesma ocorrência de análise. Para obter a definição, consulte a linha *postbacks* em  [Configuração JSON do ADBMobile](/help/android/configuration/json-config/json-config.md).

## Expansões do modelo {#section_6758AD05A24C4E9E965F5253294C164A}

As expansões do modelo estão disponíveis nas propriedades `templateurl` e `templatebody`. Os itens do modelo assumem a forma de `{key}`, em que `key` é uma chave de dados de contexto ou chave de dados tradicional. Os valores disponíveis para a expansão do modelo são apenas as [Métricas de ciclo de vida](/help/android/metrics.md), além de quaisquer dados personalizados anexados à ocorrência que aciona a mensagem. Nenhum dado baseado em histórico ou segmento está disponível no momento.

Também há modelos específicos e reservados que o SDK substituirá automaticamente por dados internos conhecidos pelo SDK.

Esta lista inclui:

| Nome do token | Descrição do token |
|--- |--- |
| {%sdkver%} | Retorna a versão do SDK. |
| {%cachebust%} | Resolve um número aleatório entre 1 e 100000000. |
| {%adid%} | Retorna a ID de anunciante do Android. Observação: funcionará apenas se tiver usado o `submitAdvertisingIdentifierTask`. |
| {%pushid%} | Retorna o token do identificador de push. Observação: funcionará apenas se tiver usado o `setPushIdentifier`. |
| {%timestampu%} | Retorna o carimbo de data e hora atual em época. |
| {%timestampz%} | Retorna o carimbo de data e hora no formato JavaScript (ISO 8601). |