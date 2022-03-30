---
description: Notas de versão e problemas conhecidos do Android SDK 4.x para Soluções da Experience Cloud.
solution: Experience Cloud Services,Analytics
title: Notas de versão
topic-fix: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
exl-id: 5cc3d031-5952-4e9b-b551-9402d3c05ccb
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 72%

---

# Notas de versão {#release-notes}

Estas são as notas de versão, problemas conhecidos e informações de hot fix do Android SDK 4.x para Soluções da Experience Cloud:

## 3 de abril de 2020: 4.18.2.

* Mensagens no aplicativo - Por motivos de segurança, WebViews criadas pelo SDK agora definem a propriedade `setAllowFileAccess` para `false`.

## 12 de março de 2020: 4.18.1

* Target - A ID de sessão do Target agora é adicionada como parâmetro de dados de contexto `a.target.sessionId` na ocorrência interna do Analytics para Target enviada para o Adobe Analytics.

## 16 de janeiro de 2020: 4.18.0

* Aquisição - Uma nova API adicionada, `Analytics.processGooglePlayInstallReferrerUrl(final String url)`, para suportar as APIs do referenciador de instalação do Google Play.

   Para obter mais informações sobre as APIs do referenciador de instalação, consulte [Ainda usando o InstallBroadcast? Alterne para a API do referenciador Play até 1º de março de 2020](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html).

## 20 de setembro de 2019: Versão 4.17.10

* Geral: Corrigida a geração de sequência de caracteres de localidade para algumas regiões no nível 21 da API do Android ou mais recente.

## 18 de julho de 2019: Versão 4.17.8

* Adobe Target: Todas as solicitações agora incluem o cliente e sessionId nos parâmetros de consulta de URL.
* Mensagens no aplicativo: Correção de um problema em que, quando uma mensagem era acionada com um URL de clickthrough vazio, os aplicativos Android travavam.
* Serviço de ID do visitante: as APIs `Visitor.appendToURL` e `Visitor.getUrlVariablesAsync` não codificam mais duas vezes seus valores de retorno.

   A codificação dupla fazia com que os valores de retorno dessas APIs fossem sinalizados por determinadas revisões de segurança.

## 6 de junho de 2019: Versão 4.17.7

* Geral - As chamadas de rede em níveis de API do Android inferiores a 20 agora usam TLS 1.1 ou TLS 1.2.
* Analytics - Status de aceitação de push anexado aos dados do ciclo de vida quando as notificações por push estão ativadas.

## 24 de maio de 2019: Versão 4.17.6

* Serviço de ID de visitante - A `setPushIdentifier` A chamada de API agora envia uma chamada de sincronização para o Serviço de ID do visitante sempre que é chamada.
* Serviço de ID de visitante - Aumento da conexão e do tempo limite de leitura de 2 segundos para 5 segundos.

Para obter mais informações sobre as notas de versão atuais e anteriores para todas as soluções, consulte [Notas de versão da Adobe Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=pt-BR).
