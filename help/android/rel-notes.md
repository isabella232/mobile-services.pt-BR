---
description: Notas de versão e problemas conhecidos do Android SDK 4.x para as Soluções da Experience Cloud.
seo-description: Notas de versão e problemas conhecidos do Android SDK 4.x para as Soluções da Experience Cloud.
seo-title: Notas de versão
solution: Marketing Cloud,Analytics
title: Notas de versão
topic: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: tm+mt
source-git-commit: 712a1107b317f02216e4df8d75fddda67a6f1feb

---


# Notas de versão {#release-notes}

Estas são as notas de versão, problemas conhecidos e informações de hot fix do Android SDK 4.x para Soluções da Experience Cloud:

**16 de janeiro de 2020: 4,18,0**

* Aquisição - Adicionada uma nova API, `Analytics.processGooglePlayInstallReferrerUrl(final String url)`para oferecer suporte às APIs de referência de instalação do Google Play.

   Para obter mais informações sobre as APIs de referência de instalação, consulte [Ainda usando o InstallBroadcast? Alterne para a API do referenciador Play até 1º de março de 2020](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html) .

**20 de setembro de 2019: Versão 4.17.10**

* Geral: Corrigida a geração de sequência de caracteres de localidade para algumas regiões no nível 21 da API do Android ou mais recente.

**18 de julho de 2019: Versão 4.17.8**

* Adobe Target: Todas as solicitações agora incluem o cliente e sessionId nos parâmetros de consulta de URL.
* Mensagens no aplicativo: correção de um problema em que, quando uma mensagem era acionada com um URL de clickthrough vazio, os aplicativos Android travavam.
* Serviço de ID do visitante: as APIs `Visitor.appendToURL` e `Visitor.getUrlVariablesAsync` não codificam mais duas vezes seus valores de retorno.

   A codificação dupla fazia com que os valores de retorno dessas APIs fossem sinalizados por determinadas revisões de segurança.

**6 de junho de 2019: Versão 4.17.7**

* Geral - As chamadas de rede em níveis de API do Android inferiores a 20 agora usam TLS 1.1 ou TLS 1.2.
* Analytics - Status de aceitação de push anexado aos dados do ciclo de vida quando as notificações por push estão ativadas.

**24 de maio de 2019: Versão 4.17.6**

* serviço de ID do visitante - A
   chamada de API `setPushIdentifier` agora envia uma chamada de sincronização para o Serviço de ID do visitante sempre que é chamada.

* Serviço de ID de visitante - Aumento da conexão e do tempo limite de leitura de 2 segundos para 5 segundos.


Para obter mais informações sobre as notas de versão atuais e anteriores para todas as soluções, consulte [Notas de versão da Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
