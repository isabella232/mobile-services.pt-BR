---
description: Essas informações ajudam a entender como as falhas são rastreadas e as práticas recomendadas para lidar com falsas falhas.
seo-description: Essas informações ajudam a entender como as falhas são rastreadas e as práticas recomendadas para lidar com falsas falhas.
seo-title: Rastrear falhas do aplicativo
solution: Experience Cloud,Analytics
title: Rastreamento de falhas do aplicativo
topic: Desenvolvedor e implementação
uuid: 4f81988b-198a-4ba9-ad53-78af90e43856
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

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

O SDK do iOS do Adobe Mobile possui um gerenciador de notificações que responde à notificação `UIApplicationDidEnterBackgroundNotification`. Neste código, um valor é definido indicando que o usuário possui o aplicativo em segundo plano. Em uma inicialização subsequente, se esse valor não puder ser encontrado, uma falha será relatada.

## Por que a medição da Adobe falha dessa maneira?

Essa abordagem de medir falhas fornece uma resposta de alto nível à pergunta: *O usuário saiu do meu aplicativo intencionalmente?*

As bibliotecas de relatórios de falhas fornecidas por empresas como a Apteligent (anteriormente, Crittercism) usam um gerenciador global `NSException` para fornecer relatórios de falhas mais detalhados. Seu aplicativo não tem permissão para ter mais de um desses tipos de manipuladores. A Adobe optou por não implementar um gerenciador global `NSException` para evitar erros no build, sabendo que nossos clientes podem estar usando outros provedores de relatórios de falhas.

## O que pode causar o relato de falhas falsas?

Os seguintes cenários são conhecidos por causar o falso relato de uma falha pelo SDK:

* Se você estiver depurando com o Xcode, inicializar o aplicativo novamente enquanto ele estiver em primeiro plano causará uma falha.

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

* No SDK 4.8.6 para iOS, código foi adicionado para determinar melhor se uma nova sessão de ciclo de vida é realmente desejada.

   Este código corrige falhas falsas #2 e #3 na seção anterior.

* Certifique-se de executar o seu desenvolvimento contra conjuntos de relatórios de não produção, o que deve evitar a ocorrência da falha falsa número 1.
* Não exclua nem modifique quaisquer valores que o SDK do Adobe Mobile coloque em `NSUserDefaults`.

   Se esses valores forem modificados fora do SDK, os dados relatados serão inválidos.

