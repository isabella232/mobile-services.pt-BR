---
description: Notas de versão e problemas conhecidos do Android SDK 4.x para as Soluções da Experience Cloud.
seo-description: Notas de versão e problemas conhecidos do Android SDK 4.x para as Soluções da Experience Cloud.
seo-title: Notas de versão
solution: Marketing Cloud,Analytics
title: Notas de versão
topic: Desenvolvedor e implementação
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# Notas de versão {#release-notes}

Estas são as notas de versão, problemas conhecidos e informações de hot fix do Android SDK 4.x para Soluções da Experience Cloud:

**September 20, 2019: Version 4.17.10**

* Geral: Corrigida a geração de sequência de caracteres de localidade para algumas regiões no nível 21 da API do Android ou mais recente.

**18 de julho de 2019: Versão 4.17.8**

* Adobe Target: Todas as solicitações agora incluem o cliente e a sessionId nos parâmetros de consulta de URL.
* Mensagens no aplicativo: correção de um problema em que, quando uma mensagem era acionada com um URL de clickthrough vazio, os aplicativos Android travavam.
* Serviço de ID do visitante: as APIs `Visitor.appendToURL` e `Visitor.getUrlVariablesAsync` não codificam mais duas vezes seus valores de retorno.

   A codificação dupla fazia com que os valores de retorno dessas APIs fossem sinalizados por determinadas revisões de segurança.

**June 6, 2019: Version 4.17.7**

* General - Networking calls on Android API levels lower than 20 will now use TLS 1.1 or TLS 1.2.
* Analytics - Appended push opt-in status to Lifecycle data when push notifications are enabled.

**May 24, 2019: Version 4.17.6**

* visitor ID Service - The
   `setPushIdentifier` A chamada de API agora envia uma chamada assíncrona para o Serviço de ID de visitante sempre que é chamada.

* Serviço de ID de visitante - Aumento da conexão e do tempo limite de leitura de 2 segundos para 5 segundos.


Para obter mais informações sobre as notas de versão atuais e anteriores para todas as soluções, consulte [Notas de versão da Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
