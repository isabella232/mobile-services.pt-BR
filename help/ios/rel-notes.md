---
description: Notas de versão e problemas conhecidos do iOS SDKs 4.x para Soluções da Experience Cloud.
seo-description: Notas de versão e problemas conhecidos do iOS SDKs 4.x para Soluções da Experience Cloud.
seo-title: Notas de versão
solution: Experience Cloud,Analytics
title: Notas de versão
topic-fix: Developer and implementation
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
exl-id: dd1e6bab-65e7-4a68-b3ec-21fb1a08aca2
translation-type: tm+mt
source-git-commit: a6663bf682f0a4283978f2f07277a4d4d43615f6
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Notas de versão {#release-notes}

Veja a seguir as notas de versão, os problemas conhecidos e as informações de hot fix dos iOS SDKs 4.x para Soluções da Experience Cloud:

**13 de abril de 2021: Versão 4.21.2**

* Serviço de ID do visitante - Correção de um problema em que identificadores de anúncios vazios eram sincronizados com o Serviço de ID do visitante.

**13 de janeiro de 2021: Versão 4.21.1**

* Geral: correção de um problema que causava exceções do SQLite durante o encerramento do aplicativo.

**15 de dezembro de 2020: Versão 4.21.0**

* Geral - O SDK agora é distribuído usando o XCFrameworks para dar suporte a hardware com a nova arquitetura Apple M1 e, ao mesmo tempo, manter o suporte para a arquitetura Intel existente.
   * IMPORTANTE: a atualização para o AdobeMobile XCFrameworks requer o Xcode 12.0 ou mais recente
   * IMPORTANTE: se estiver usando Cocoapods, a atualização para o AdobeMobile XCFrameworks exigirá o Cocoapods 1.10.0 ou mais recente

**4 de novembro de 2020: Versão 4.20.0**

* Serviço de ID do visitante - Adição de um parâmetro de status device_consent quando setAdvertisingIdentifier é chamado depois que o rastreamento de anúncio é ativado/desativado.
* Analytics - Correção de um erro que impedia o envio de ocorrências do Analytics em uma instalação quando o iAd.framework estava vinculado e o dispositivo tinha “Rastreamento limitado de anúncios” ativado.

**16 de julho de 2020: Versão 4.19.3**

* Geral - Correção de um erro que impedia que URLs de deep link com vários parâmetros de query de logon fossem manipulados adequadamente.

**24 de março de 2020: Versão 4.19.2**

* Geral - Correção de alguns vazamentos no código do Target.

**12 de março de 2020: Versão 4.19.1**

* Geral - Resolução de uma possível falha quando as enumerações Swift são incluídas nos dados de contexto para chamadas de rastreamento.
* Target - Agora a ID de sessão do target será adicionada como parâmetro de dados de contexto &quot;a.target.sessionId&quot; na ocorrência interna do Analytics para Target enviada para o Adobe Analytics.

**4 de fevereiro de 2020: Versão 4.19.0**

* Ciclo de vida - Uma nova API adicionada, pauseCollectingLifecycleData, para mitigar os dados de duração da sessão anormais reportados em alguns dispositivos iOS antigos.

**8 de novembro de 2019: Versão 4.18.9**

* Em Mensagens do aplicativo - correção de um erro em que imagens armazenadas em cache ou agrupadas não podiam ser carregadas nas mensagens de tela cheia.

**20 de setembro de 2019: Versão 4.18.8**

* Mensagens no aplicativo:

   * Em dispositivos que executam o iOS 10 ou mais recente, a estrutura `UserNotifications` agora é usada para agendar notificações locais para aplicativos vinculados ao `UserNotifications.framework`.
   * As mensagens de tela cheia agora usam WKWebViews do `WebKit.framework`, que devem ser vinculadas no projeto Xcode.
   * Correção de um erro em que a carga de click-through de push não podia ser usada como característica das mensagens no aplicativo.
   * Correção de uma falha.

* Geral - Correção de um erro em que os dados do SDK tinham sido sincronizados ao aplicativo watchOS emparelhado em cada chamada do Analytics.

**2 de agosto de 2019: Versão 4.18.7**

* Reversão de uma alteração introduzida na versão 4.18.6 que, em alguns ambientes, causou uma falha em dispositivos que executavam uma versão do iOS anterior à 11.0.

* Adobe Target: inclusão da propriedade `requestLocationParameters` em `ADBTargetRequestObject`, que permite que a impressionId seja enviada com solicitações do Target.

**18 de julho de 2019: Versão 4.18.6**

* Adobe Target: todas as solicitações agora incluem o cliente e o `sessionId` nos parâmetros de consulta de URL.
* Adobe Target: correção de um vazamento de memória.
* Serviço de ID do visitante: as APIs `visitorAppendToURL` e `visitorGetUrlVariablesAsync` não codificam mais duas vezes seus valores de retorno.

   A codificação dupla fazia com que os valores de retorno dessas APIs fossem sinalizados por determinadas revisões de segurança.

**5 de junho de 2019: Versão 4.18.5**

* Analytics - Anexa-se o status de aceitação por push aos dados do ciclo de vida quando as notificações por push estiverem ativadas.

**24 de maio de 2019: Versão 4.18.4**

* Serviço de ID do visitante - Aumento do tempo limite de retorno para a API
   `visitorGetUrlVariablesAsync` para 30 segundos.

* Serviço de ID do visitante - A chamada da API `setPushIdentifier` agora envia uma chamada de sincronização para o Serviço de ID do visitante sempre que é chamada.

Para obter mais informações sobre as notas de versão atuais e anteriores para todas as soluções, consulte [Notas de versão da Adobe Experience Cloud](https://docs.adobe.com/content/help/pt-BR/release-notes/experience-cloud/current.html).
