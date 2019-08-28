---
description: Os SDKs do Experience Cloud Mobile oferecem APIs prontas para o Regulamento Geral sobre a Proteção de Dados (GDPR) para controladores que permitem aos usuários recuperar identidades armazenadas localmente e definir sinalizadores de status de opção para coleta e transmissão de dados.
seo-description: Os SDKs do Experience Cloud Mobile oferecem APIs prontas para o Regulamento Geral sobre a Proteção de Dados (GDPR) para controladores que permitem aos usuários recuperar identidades armazenadas localmente e definir sinalizadores de status de opção para coleta e transmissão de dados.
seo-title: Privacidade e visão geral do Regulamento geral de proteção de dados
title: Privacidade e visão geral do Regulamento geral de proteção de dados
uuid: 56 d 6 f 155-efec -4 b 3 f-a 972-a 63155729167
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Privacy and General Data Protection Regulation overview {#privacy-and-general-data-protection-regulation}

Os SDKs do Experience Cloud Mobile oferecem APIs prontas para o Regulamento Geral sobre a Proteção de Dados (GDPR) para controladores que permitem aos usuários recuperar identidades armazenadas localmente e definir sinalizadores de status de opção para coleta e transmissão de dados.

## Nova versão do SDK da Adobe Experience Cloud

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

>[!IMPORTANT]
>
>Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para começar, acesse o [Launch](https://launch.adobe.com/).
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

Quando a Adobe oferece software e serviços para uma empresa, ela age como um processador de dados de quaisquer dados pessoais que processa e armazena como parte do oferecimento desses serviços. Como processador de dados, a Adobe processa dados pessoais de acordo com a permissão e as instruções de sua empresa (por exemplo, como definido em seu contrato com a Adobe).

Como controlador de dados, você pode usar os SDKs dos Adobe Mobile Services para oferecer suporte às solicitações de recuperação e exclusão de GDPR de seus aplicativos móveis.

Nas partes do SDK do Adobe Mobile em seus aplicativos móveis, é possível usar as configurações e os métodos a seguir:

* Para recuperar os dados dos SDKs e enviar esses dados para seus servidores, use o método `getAllIdentifiersAsync`.

   Para obter mais informações, consulte [Recuperar identificadores armazenados](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md).

* Para definir o status de opção e ajudá-lo com a solicitação de exclusão de dados do GDPR, use as seguintes configurações:

   * `privacyDefault`
   * `setPrivacyStatus`
   Para obter mais informações, consulte [Definir o status de opção do usuário](/help/android/c-mob-privacy-gdpr-android/privacy.md).