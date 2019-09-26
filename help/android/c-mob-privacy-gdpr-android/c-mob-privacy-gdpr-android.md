---
description: Os SDKs do Experience Cloud Mobile oferecem APIs prontas para o Regulamento Geral sobre a Proteção de Dados (GDPR) para controladores que permitem aos usuários recuperar identidades armazenadas localmente e definir sinalizadores de status de opção para coleta e transmissão de dados.
seo-description: Os SDKs do Experience Cloud Mobile oferecem APIs prontas para o Regulamento Geral sobre a Proteção de Dados (GDPR) para controladores que permitem aos usuários recuperar identidades armazenadas localmente e definir sinalizadores de status de opção para coleta e transmissão de dados.
seo-title: Visão geral do Regulamento de privacidade e proteção geral de dados
title: Visão geral do Regulamento de privacidade e proteção geral de dados
uuid: 56d6f155-efec-4b3f-a972-a63155729167
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Privacy and General Data Protection Regulation overview {#privacy-and-general-data-protection-regulation}

Os SDKs do Experience Cloud Mobile oferecem APIs prontas para o Regulamento Geral sobre a Proteção de Dados (GDPR) para controladores que permitem aos usuários recuperar identidades armazenadas localmente e definir sinalizadores de status de opção para coleta e transmissão de dados.

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* To get started, go to Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Visão geral

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

Quando a Adobe oferece software e serviços para uma empresa, ela age como um processador de dados de quaisquer dados pessoais que processa e armazena como parte do oferecimento desses serviços. Como processador de dados, a Adobe processa dados pessoais de acordo com a permissão e as instruções de sua empresa (por exemplo, como definido em seu contrato com a Adobe).

Como controlador de dados, você pode usar os SDKs dos Adobe Mobile Services para oferecer suporte às solicitações de recuperação e exclusão de GDPR de seus aplicativos móveis.

Nas partes do SDK do Adobe Mobile em seus aplicativos móveis, é possível usar as configurações e os métodos a seguir:

* Para recuperar os dados dos SDKs e enviar esses dados para seus servidores, use o método `getAllIdentifiersAsync`.

   For more information, see Retrieving Stored Identifiers.[](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)

* Para definir o status de opção e ajudá-lo com a solicitação de exclusão de dados do GDPR, use as seguintes configurações:

   * `privacyDefault`
   * `setPrivacyStatus`
   Para obter mais informações, consulte [Configuração do status](/help/android/c-mob-privacy-gdpr-android/privacy.md)de opção do usuário.