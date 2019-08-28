---
description: Notas de versão e problemas conhecidos dos SDKs do iOS 4.x para as Soluções da Experience Cloud.
seo-description: Notas de versão e problemas conhecidos dos SDKs do iOS 4.x para as Soluções da Experience Cloud.
seo-title: Notas de versão
solution: Marketing Cloud,Analytics
title: Notas de versão
topic: Desenvolvedor e implementação
uuid: e 1613 dc 5-02 a 4-43 a 7-997 a -29 b 4 de 98 b 4 d 1
translation-type: tm+mt
source-git-commit: 80a60276f9926177c8958b8e87e9393a83e7e6a9

---


# Notas de versão {#release-notes}

Estas são as notas de versão, problemas conhecidos e informações de hot fix para iOS sdks 4. x para Soluções da Experience Cloud:

**: de agosto de 2019: Versão 4.18.7**

* Revertido uma alteração introduzida na versão 4.18.6 que, em alguns ambientes, causava uma falha em dispositivos que executavam uma versão do iOS anterior à 11.0.

* Adobe Target: Adicionada `requestLocationParameters` a propriedade em `ADBTargetRequestObject`, que permite que a impressionid seja enviada com solicitações do Target.

**: 8 de julho de 28 19: Versão 4.18.6**

* Adobe Target: todas as solicitações agora incluem o cliente e o `sessionId` nos parâmetros de consulta de URL.
* Adobe Target: correção de um vazamento de memória.
* Serviço de ID do visitante: as APIs `visitorAppendToURL` e `visitorGetUrlVariablesAsync` não codificam mais duas vezes seus valores de retorno.

   A codificação dupla fazia com que os valores de retorno dessas APIs fossem sinalizados por determinadas revisões de segurança.

**: de junho de 2019: Versão 4.18.5**

* Analytics - Anexe o status de aceitação de push aos dados do ciclo de vida quando as notificações por push estiverem ativadas.

**: 4 de maio de 2019: Versão 4.18.4**

* Serviço de ID do visitante - o tempo limite de retorno para a variável
   `visitorGetUrlVariablesAsync` API a 30 segundos.

* Serviço de ID de visitante - a `setPushIdentifier` chamada de API agora envia uma chamada de sincronização para o Serviço de ID de visitante toda vez que é chamada.

Para obter mais informações sobre as notas de versão atuais e anteriores para todas as soluções, consulte [Notas de versão da Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
