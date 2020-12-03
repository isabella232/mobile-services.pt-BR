---
description: Essas informações ajudam a entender como as falhas são rastreadas e as práticas recomendadas para lidar com falsas falhas.
seo-description: Essas informações ajudam a entender como as falhas são rastreadas e as práticas recomendadas para lidar com falsas falhas.
seo-title: Rastrear falhas do aplicativo
solution: Experience Cloud,Analytics
title: Rastreamento de falhas do aplicativo
topic: Developer and implementation
uuid: 4f81988b-198a-4ba9-ad53-78af90e43856
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 100%

---


# Rastreamento de falhas do aplicativo {#track-app-crashes}

Essas informações ajudam a entender como as falhas são rastreadas e as práticas recomendadas para lidar com falsas falhas.

>[!IMPORTANT]
>
>Você deve atualizar para o SDK do iOS versão 4.8.6, que contém alterações críticas que impedem que falhas falsas sejam relatadas.

## Quando a Adobe relata uma falha?

Se o seu aplicativo for encerrado sem antes ter sido colocado em segundo plano, o SDK relata uma falha na próxima vez que o aplicativo for inicializado.

## Como funciona o relatório de falhas?

O iOS usa as notificações do sistema, que permitem aos desenvolvedores rastrear e responder a diferentes estados e eventos no ciclo de vida do aplicativo.

O SDK do iOS do Adobe Mobile possui um gerenciador de notificações que responde à notificação `UIApplicationDidEnterBackgroundNotification`. Neste código, um valor é definido indicando que o usuário colocou o aplicativo em segundo plano. Na próxima inicialização, se esse valor não for encontrado, uma falha será relatada.

## Por que a medição da Adobe falha dessa maneira?

Essa abordagem de medir falhas fornece uma resposta de alto nível à pergunta: *O usuário saiu do meu aplicativo intencionalmente?*

As bibliotecas de relatórios de falhas fornecidas por empresas como a Apteligent (anteriormente, Crittercism) usam um gerenciador global `NSException` para fornecer relatórios de falhas mais detalhados. Seu aplicativo não tem permissão para ter mais de um desses tipos de manipuladores. A Adobe optou por não implementar um gerenciador global `NSException` para evitar erros no build, sabendo que nossos clientes podem estar usando outros provedores de relatórios de falhas.

## O que pode causar o relato de falhas falsas?

Os cenários a seguir são conhecidos por causar falsamente uma falha informada pelo SDK:

* Se você estiver depurando com o Xcode, iniciar o aplicativo novamente enquanto ele estiver em primeiro plano causará uma falha.

   >[!TIP]
   >
   >É possível evitar uma falha neste cenário, colocando o aplicativo em segundo plano antes de iniciá-lo novamente no Xcode.

* Se o aplicativo estiver em segundo plano e enviar ocorrências do Analytics por meio de uma chamada diferente de `trackActionFromBackground`, `trackLocation`, ou `trackBeacon`, e o aplicativo for encerrado (manualmente ou pelo sistema operacional) enquanto estiver em segundo plano, a próxima inicialização causará uma falha.

   >[!TIP]
   >
   >A atividade em segundo plano que ocorre além do limite `lifecycleTimeout` também pode resultar em uma inicialização falsa adicional.

* Se o aplicativo for inicializado em segundo plano (como resultado de uma busca em segundo plano, atualização de localização e outros) e for encerrado pelo sistema operacional sem nunca passar para o primeiro plano, a próxima inicialização (em segundo ou primeiro plano) resultará em uma falha.
* Se você excluir programaticamente o sinalizador de pausa da Adobe do `NSUserDefaults` enquanto o aplicativo estiver em segundo plano, a próxima inicialização ou retomada causará uma falha.

## Como impedir o relato de falhas falsas?

As seguintes práticas podem ajudá-lo a evitar que falhas falsas sejam relatadas:

* No iOS SDK 4.8.6, o código foi adicionado para determinar melhor se uma nova sessão do ciclo de vida é realmente desejada.

   Este código corrige as falhas falsas nº 2 e nº 3 na seção anterior.

* Faça o desenvolvimento em conjuntos de relatórios de não produção, o que deve impedir a ocorrência de falhas falsas nº 1.
* Não exclua nem modifique quaisquer valores que o SDK do Adobe Mobile coloque em `NSUserDefaults`.

   Se esses valores forem modificados fora do SDK, os dados relatados serão inválidos.

