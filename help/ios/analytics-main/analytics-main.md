---
description: Essas informações ajudam a usar o iOS SDK com o Adobe Analytics.
solution: Experience Cloud Services,Analytics
title: Visão geral do Analytics
topic-fix: Developer and implementation
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
exl-id: 7c383b1d-2e59-4473-9de5-80c84d896f6d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 95%

---

# Visão geral do Analytics {#analytics}

As informações nesta seção ajudam a usar o iOS SDK com o Adobe Analytics.

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para obter a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Criação de identificadores de rastreamento do Analytics

Nos SDKs, os identificadores são usados para rastrear usuários, e esta é a hierarquia de identificadores:

1. Identificador de visitante personalizado (VID)
1. Identificador de rastreamento do Analytics (AID)
1. Identificador da Experience Cloud (MID)

>[!TIP]
>
>A sigla correta para Identificador da Experience Cloud é ECID. Embora os SDKs ainda usem MID, esse é o nome antigo.

O AID, que às vezes também é chamado de identificador de rastreamento, é gerado pelo SDK quando o aplicativo não está configurado para usar um MID. O valor persiste entre inicializações e atualizações de aplicativos em `NSUserDefaults`. Se o usuário excluir o aplicativo do dispositivo e reinstalar o aplicativo, ou se o desenvolvedor do aplicativo limpar `NSUserDefaults`, um novo identificador é gerado pelo SDK. Esse processo resulta em um novo usuário nos relatórios do Analytics.

Para usuários em um aplicativo que introduz o suporte ao serviço de identidade (MID), os valores de AID existentes são enviados com ocorrências do Analytics e a ocorrência do Analytics contém um AID e uma MID. Para novos usuários em um aplicativo com suporte ao serviço de identidade, as solicitações do Analytics contêm apenas uma MID. Para obter mais informações sobre como identificar visitantes, consulte [Visitantes únicos](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=pt-BR) na documentação do Adobe Analytics.
