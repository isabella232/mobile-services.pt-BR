---
description: Os SDKs móveis da Experience Cloud oferecem aos controladores APIs prontas para o Regulamento Geral sobre a Proteção de Dados (GDPR), que permitem aos usuários recuperar identidades armazenadas localmente e definir sinalizadores de status de opção para a coleta e a transmissão de dados.
title: Privacidade e visão geral do Regulamento Geral sobre a Proteção de Dados
uuid: 56d6f155-efec-4b3f-a972-a63155729167
exl-id: 57696f2e-87f4-4f72-bec2-80c7192576f9
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 76%

---

# Privacidade e visão geral do Regulamento Geral sobre a Proteção de Dados {#privacy-and-general-data-protection-regulation}

Os SDKs móveis da Experience Cloud oferecem aos controladores APIs prontas para o Regulamento Geral sobre a Proteção de Dados (GDPR), que permitem aos usuários recuperar identidades armazenadas localmente e definir sinalizadores de status de opção para a coleta e a transmissão de dados.

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para obter a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Visão geral

>[!IMPORTANT]
>
>O GDPR é compatível **somente** com o SDK móvel versão 4.16.0 ou posterior.

Quando o Adobe fornece software e serviços para uma empresa, ele age como um processador de dados para quaisquer dados pessoais que processa e armazena como parte do fornecimento desses serviços. Como processador de dados, o Adobe processa dados pessoais de acordo com a permissão e as instruções de sua empresa (por exemplo, como definido em seu contrato com o Adobe).

Como controlador de dados, você pode usar os SDKs do Adobe Mobile Services para suportar solicitações de recuperação e exclusão de GDPR de seus aplicativos móveis.

Nas partes do SDK do Adobe Mobile em seus aplicativos móveis, é possível usar as configurações e os métodos a seguir:

* Para recuperar os dados dos SDKs e enviar esses dados para seus servidores, use o método `getAllIdentifiersAsync`.

   Para obter mais informações, consulte [Recuperação de identificadores armazenados](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md).

* Para definir o status de opção e ajudá-lo com a solicitação de exclusão de dados do GDPR, use as seguintes configurações:

   * `privacyDefault`
   * `setPrivacyStatus`
   Para obter mais informações, consulte [Configuração do status de opção do usuário](/help/android/c-mob-privacy-gdpr-android/privacy.md).
