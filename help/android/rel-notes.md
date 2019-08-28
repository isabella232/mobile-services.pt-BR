---
description: Notas de versão e problemas conhecidos do Android SDK 4.x para as Soluções da Experience Cloud.
seo-description: Notas de versão e problemas conhecidos do Android SDK 4.x para as Soluções da Experience Cloud.
seo-title: Notas de versão
solution: Marketing Cloud,Analytics
title: Notas de versão
topic: Desenvolvedor e implementação
uuid: 16 bb 4 de 8-a 216-47 a 8-928 c -0 b 1 e 1421 adcf
translation-type: tm+mt
source-git-commit: 4c68e3fb3687a555fc7fdfa50a42e837b76a7d88

---


# Notas de versão {#release-notes}

Estas são as notas de versão, os problemas conhecidos e as informações de hot fix do Android SDK 4. x para as Soluções da Experience Cloud:

**: de agosto de 2019: Versão 4.17.9**

* Serviço de ID do visitante: Corrigida `StrictMode` a violação ao chamar syncidentifiers.

   Essa violação foi causada pela leitura das preferências compartilhadas no thread principal.

* Adobe Target: Adicionado o `requestLocationParameters` atributo no `TargetRequestObject`, o qual permite que a impressionid seja enviada com solicitações do Target.

**: 8 de julho de 28 19: Versão 4.17.8**

* Adobe Target: Todas as solicitações agora incluem o cliente e a sessionid nos parâmetros de consulta de URL.
* Mensagens no aplicativo: correção de um problema em que, quando uma mensagem era acionada com um URL de clickthrough vazio, os aplicativos Android travavam.
* Serviço de ID do visitante: as APIs `Visitor.appendToURL` e `Visitor.getUrlVariablesAsync` não codificam mais duas vezes seus valores de retorno.

   A codificação dupla fazia com que os valores de retorno dessas APIs fossem sinalizados por determinadas revisões de segurança.

**: de junho de 2019: Versão 4.17.7**

* Geral - As chamadas de rede em níveis de API do Android inferiores a 20 usarão TLS 1.1 ou TLS 1.2.
* Analytics - status de aceitação de push anexado para dados de ciclo de vida quando as notificações por push são ativadas.

**: 4 de maio de 2019: Versão 4.17.6**

* serviço de ID de visitante - o
   `setPushIdentifier` A chamada de API agora envia uma
chamada de sincronização para o Serviço de ID de visitante toda vez que é chamada.

* Serviço de ID do visitante - aumentou o tempo limite e leia
o tempo limite de 2 segundos para 5 segundos.


Para obter mais informações sobre as notas de versão atuais e anteriores para todas as soluções, consulte [Notas de versão da Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
