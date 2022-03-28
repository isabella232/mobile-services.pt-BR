---
description: Os SDKs móveis da Experience Cloud oferecem aos controladores APIs prontas para o Regulamento Geral sobre a Proteção de Dados (GDPR), que permitem aos usuários recuperar identidades armazenadas localmente e definir sinalizadores de status de opção para a coleta e a transmissão de dados.
title: Privacidade e Regulamento Geral sobre a Proteção de Dados
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
exl-id: 8549310d-31b8-49a3-9276-f8e9ab980a10
source-git-commit: bd55e3525488f24bc9845220f0df62706ec28f31
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 74%

---

# Privacidade e Regulamento Geral sobre a Proteção de Dados {#privacy-and-general-data-protection-regulation}

Os SDKs móveis da Experience Cloud oferecem aos controladores APIs prontas para o Regulamento Geral sobre a Proteção de Dados (GDPR), que permitem aos usuários recuperar identidades armazenadas localmente e definir sinalizadores de status de opção para a coleta e a transmissão de dados.

>[!IMPORTANT]
>
>**Somente** o SDK móvel versão 4.16.0 ou posterior é compatível com o GDPR.

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para obter a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Visão geral

Quando o Adobe fornece software e serviços para uma empresa, ele age como um processador de dados para quaisquer dados pessoais que processa e armazena como parte do fornecimento desses serviços. Como processador de dados, o Adobe processa dados pessoais de acordo com a permissão e as instruções de sua empresa (por exemplo, como definido em seu contrato com o Adobe).

Como controlador de dados, você pode usar os SDKs de serviços da Adobe Mobile para suportar solicitações de recuperação e exclusão de GDPR de seus aplicativos móveis.

Nas partes do SDK do Adobe Mobile em seus aplicativos móveis, é possível usar as configurações e os métodos a seguir:

* Para recuperar os dados dos SDKs e enviar esses dados para seus servidores, use o método `getAllIdentifiersAsync`.

   Para obter mais informações, consulte [Recuperação de identificadores armazenados](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md).

* Para definir o status de opção e ajudá-lo com a solicitação de exclusão de dados do GDPR, use as seguintes configurações:

   * `privacyDefault`
   * `setPrivacyStatus`

   Para obter mais informações, consulte [Configuração do status de opção do usuário](/help/ios/c-mob-privacy-gdpr-ios/privacy.md).

## Informações adicionais {#section_7C7124C50D85469C8C8714533FB1A37D}

* Para obter mais informações sobre o GDPR, consulte [GDPR e seu negócio](https://www.adobe.com/br/privacy/general-data-protection-regulation.html).
