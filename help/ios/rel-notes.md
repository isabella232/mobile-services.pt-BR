---
description: Notas de versão e problemas conhecidos dos SDKs do iOS 4.x para as Soluções da Experience Cloud.
seo-description: Notas de versão e problemas conhecidos dos SDKs do iOS 4.x para as Soluções da Experience Cloud.
seo-title: Notas de versão
solution: Marketing Cloud,Analytics
title: Notas de versão
topic: Desenvolvedor e implementação
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# Notas de versão {#release-notes}

Estas são as notas de versão, os problemas conhecidos e as informações de hot fix para iOS SDKs 4.x para Soluções da Experience Cloud:

**20 de setembro de 2019: Versão 4.18.8**

* Em mensagens do aplicativo:

   * On devices running iOS 10 or newer, the  framework is now used to schedule local notifications for apps that are linked to the .`UserNotifications``UserNotifications.framework`
   * As mensagens de tela inteira agora usam WKWebViews de `WebKit.framework`, que devem ser vinculadas no projeto Xcode.
   * Correção de um bug no qual a carga de click-through de push não podia ser usada como características para mensagens no aplicativo.
   * Corrigido um problema de falha.

* Geral - Corrigido um erro no qual os dados do SDK eram sincronizados com o aplicativo WatchOS emparelhado em cada chamada do Analytics.

**2 de agosto de 2019: Versão 4.18.7**

* Reversão de uma alteração introduzida na versão 4.18.6 que, em alguns ambientes, causou uma falha em dispositivos que executavam uma versão do iOS anterior à 11.0.

* Adobe Target: Adicionada a `requestLocationParameters` propriedade em `ADBTargetRequestObject`, que permite que a impressãoId seja enviada com solicitações do Target.

**July 18, 2019: Version 4.18.6**

* Adobe Target: todas as solicitações agora incluem o cliente e o `sessionId` nos parâmetros de consulta de URL.
* Adobe Target: correção de um vazamento de memória.
* Serviço de ID do visitante: as APIs `visitorAppendToURL` e `visitorGetUrlVariablesAsync` não codificam mais duas vezes seus valores de retorno.

   A codificação dupla fazia com que os valores de retorno dessas APIs fossem sinalizados por determinadas revisões de segurança.

**5 de junho de 2019: Versão 4.18.5**

* Analytics - Append push opt-in status to Lifecycle data when push notifications are enabled.

**May 24, 2019: Version 4.18.4**

* Serviço de ID de visitante - Aumento do tempo limite de retorno para o
   `visitorGetUrlVariablesAsync` API em 30 segundos.

* Serviço de ID do visitante - A chamada `setPushIdentifier` da API agora envia uma chamada de sincronização para o Serviço de ID do visitante sempre que é chamada.

Para obter mais informações sobre as notas de versão atuais e anteriores para todas as soluções, consulte [Notas de versão da Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
