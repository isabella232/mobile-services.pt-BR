---
description: Os SDKs do Experience Cloud Mobile oferecem APIs prontas para o Regulamento Geral sobre a Proteção de Dados (GDPR) para controladores que permitem aos usuários recuperar identidades armazenadas localmente e definir sinalizadores de status de opção para coleta e transmissão de dados.
seo-description: Os SDKs do Experience Cloud Mobile oferecem APIs prontas para o Regulamento Geral sobre a Proteção de Dados (GDPR) para controladores que permitem aos usuários recuperar identidades armazenadas localmente e definir sinalizadores de status de opção para coleta e transmissão de dados.
seo-title: Privacidade e Regulamento Geral sobre a Proteção de Dados
title: Privacidade e Regulamento Geral sobre a Proteção de Dados
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Privacidade e Regulamento Geral sobre a Proteção de Dados {#privacy-and-general-data-protection-regulation}

Os SDKs do Experience Cloud Mobile oferecem APIs prontas para o Regulamento Geral sobre a Proteção de Dados (GDPR) para controladores que permitem aos usuários recuperar identidades armazenadas localmente e definir sinalizadores de status de opção para coleta e transmissão de dados.

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

Quando a Adobe oferece software e serviços para uma empresa, ela age como um processador de dados de quaisquer dados pessoais que processa e armazena como parte do oferecimento desses serviços. Como processador de dados, a Adobe processa dados pessoais de acordo com a permissão e as instruções de sua empresa (por exemplo, como definido em seu contrato com a Adobe).

Como controlador de dados, você pode usar os SDKs dos Adobe Mobile Services para oferecer suporte às solicitações de recuperação e exclusão de GDPR de seus aplicativos móveis.

## Nova versão do SDK da Adobe Experience Cloud

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para começar, acesse o Launch.
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Para obter mais informações, consulte [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).


Nas partes do SDK do Adobe Mobile em seus aplicativos móveis, é possível usar as configurações e os métodos a seguir:

* Para recuperar os dados dos SDKs e enviar esses dados para seus servidores, use o método `getAllIdentifiersAsync`.

   Para obter mais informações, consulte [Recuperando identificadores](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)armazenados.

* Para definir o status de opção e ajudá-lo com a solicitação de exclusão de dados do GDPR, use as seguintes configurações:

   * `privacyDefault`
   * `setPrivacyStatus`
   Para obter mais informações, consulte [Configuração do status](/help/ios/c-mob-privacy-gdpr-ios/privacy.md)de opção do usuário.

## Informações adicionais {#section_7C7124C50D85469C8C8714533FB1A37D}

* Para obter mais informações sobre o GDPR, consulte [GDPR e seus negócios](https://www.adobe.com/privacy/general-data-protection-regulation.html).
* Para consultar a documentação da API do GDPR, acesse [API do Regulamento Geral sobre a Proteção de Dados](https://adobe.io/apis/cloudplatform/gdpr.html).

