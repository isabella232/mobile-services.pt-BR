---
description: O Android SDK 4.x para Soluções da Experience Cloud permite medir aplicativos nativos do Android, fornecer conteúdos direcionados no aplicativo e aproveitar e coletar dados do público pelo gerenciamento de público.
keywords: android;library;mobile;sdk
seo-description: O Android SDK 4.x para Soluções da Experience Cloud permite medir aplicativos nativos do Android, fornecer conteúdos direcionados no aplicativo e aproveitar e coletar dados do público pelo gerenciamento de público.
seo-title: Android SDK 4.x para Soluções da Experience Cloud
solution: Experience Cloud,Analytics
title: Android SDK 4.x para Soluções da Experience Cloud
topic: Developer and implementation
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
translation-type: tm+mt
source-git-commit: bc11c1e7a4a11657ee89c40ddcbd37377ce50bb5
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 100%

---


# Android SDK 4.x para Soluções da Experience Cloud {#android-sdk-x-for-experience-cloud-solutions}

O Android SDK 4.x para Soluções da Experience Cloud permite medir aplicativos nativos do Android, fornecer conteúdos direcionados no aplicativo e aproveitar e coletar dados do público pelo gerenciamento de público.

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para obter a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>O SKU do Adobe Analytics Mobile Marketing Add-on é necessário para habilitar o Mobile Services para aquisição móvel, deep linking, geolocalização e mensagens móveis. Para obter mais informações, entre em contato com seu CSM da Adobe.

>[!IMPORTANT]
>
>Embora você possa configurar os recursos na interface do usuário, eles não funcionarão até você baixar o arquivo de configuração gerado e adicioná-lo ao SDK. Para obter informações sobre como baixar e configurar os SDKs, consulte [Implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).

Os SDKs são compatíveis com as seguintes versões do Android:

* A versão 4.6.0 ou anterior é compatível com Android 2.2 (API 8) - Android 5.1.1 (API 22)
* A versão 4.6.1 ou posterior é compatível com Android 2.3 (API 9) ou posterior

Algumas informações para lembrar:

* Na versão 4.2 e posterior, todas as ocorrências são enviadas usando HTTP POST.

   Isso não afeta os dados coletados ou relatados, mas você deve usar um analisador de pacotes compatível com a inspeção de dados POST para ver as ocorrências.

* Se estiver atualizando de uma versão anterior, consulte o [Guia de migração 4.x](/help/android/getting-started/migration-v3.md).

## Documentação do usuário do Adobe Mobile {#section_7583FD5FDED143619048E9744A3F2D21}

O Adobe Mobile Services fornece uma interface do usuário que reúne recursos de marketing móveis para aplicativos móveis na Adobe Experience Cloud. Para saber mais sobre a interface do usuário do Adobe e ler a documentação do usuário, consulte [Adobe Mobile Services](https://docs.adobe.com/content/help/br/mobile-services/using/home.html).

## Notas de versão {#section_F8181DC052D44DD2A99AB40A41F6792C}

Para obter as últimas informações sobre os lançamentos da Experience Cloud, consulte [Notas de versão da Experience Cloud](https://docs.adobe.com/content/help/pt-BR/release-notes/experience-cloud/current.html).

## Usar o Bloodhound

>[!IMPORTANT]
>
>Em **30 de abril de 2017**, o Adobe Bloodhound foi interrompido. A partir de 1º de maio de 2017, não serão fornecidos aprimoramentos e suporte adicionais pela engenharia ou pelo Adobe Expert Care.
