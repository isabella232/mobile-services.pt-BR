---
description: Os postbacks permitem enviar dados coletados pelo SDK para um servidor de terceiros. Ao usar os mesmos acionadores e características usadas para exibir uma mensagem no aplicativo, é possível configurar o SDK para enviar dados personalizados a um destino de terceiros.
keywords: android;biblioteca;móvel;sdk
seo-description: Os postbacks permitem enviar dados coletados pelo SDK para um servidor de terceiros. Ao usar os mesmos acionadores e características usadas para exibir uma mensagem no aplicativo, é possível configurar o SDK para enviar dados personalizados a um destino de terceiros.
seo-title: Postbacks
solution: Experience Cloud,Analytics
title: Visão geral de postbacks
topic: Desenvolvedor e implementação
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
translation-type: ht
source-git-commit: f26dcd5cf9b19de49c9d034c854d9738c7843fb2

---


# Postbacks {#postbacks}

Os postbacks permitem enviar dados coletados pelo SDK para um servidor de terceiros. Ao usar os mesmos acionadores e características usadas para exibir uma mensagem no aplicativo, é possível configurar o SDK para enviar dados personalizados a um destino de terceiros.

>[!IMPORTANT]
>
>Essa funcionalidade exige a versão 4.6.0 ou posterior do SDK.

As mensagens de postback são enfileiradas e seguem todas as regras online/offline existentes que regem a coleta de dados analíticos. Quando uma mensagem corresponde (como correspondem as mensagens exibidas), as mensagens de postback não cancelam o resto das mensagens. Isso permite que vários postbacks ocorram na mesma ocorrência de análise. Para obter a definição, consulte a linha *postbacks* em [Configuração JSON do ADBMobile](/help/android/configuration/json-config/json-config.md).

## Expansões do modelo {#section_6758AD05A24C4E9E965F5253294C164A}

As expansões do modelo estão disponíveis nas propriedades `templateurl` e `templatebody`. Os itens do modelo assumem a forma de `{key}`, em que `key` é uma chave de dados de contexto ou chave de dados tradicional. Os valores disponíveis para a expansão do modelo são apenas as [Métricas de ciclo de vida](/help/android/metrics.md), além de quaisquer dados personalizados anexados à ocorrência que aciona a mensagem. Nenhum dado baseado em histórico ou em segmentos está disponível no momento.

Há também modelos específicos e reservados que o SDK substituirá automaticamente com dados internos conhecidos pelo SDK.

A lista inclui:

| Nome do token: | Descrição do token |
|--- |--- |
| {%sdkver%} | Retorna a versão do SDK. |
| {%cachebust%} | Resolve um número aleatório entre 1 e 100000000. |
| {%adid%} | Retorna a ID de anunciante do Android. Observação: funcionará apenas se tiver usado o `submitAdvertisingIdentifierTask`. |
| {%pushid%} | Retorna o token do identificador de push. Observação: funcionará apenas se tiver usado o `setPushIdentifier`. |
| {%timestampu%} | Retorna o carimbo de data e hora atual em época. |
| {%timestampz%} | Retorna o carimbo de data e hora no formato JavaScript (ISO 8601). |