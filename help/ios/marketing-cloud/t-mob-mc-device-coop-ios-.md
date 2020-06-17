---
description: Para começar a usar o Device Co-op da Experience Cloud, entre em contato com o representante da Adobe.
seo-description: Para começar a usar o Device Co-op da Experience Cloud, entre em contato com o representante da Adobe.
seo-title: Device Co-op da Experience Cloud
title: Device Co-op da Experience Cloud
uuid: 434a6f8f-ec24-439d-95f0-a246b384b3b5
translation-type: tm+mt
source-git-commit: 86ba045b44bf6553e80727c0d61ccdd9a552d16c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 90%

---


# Device Co-op da Experience Cloud {#experience-cloud-device-co-op}

Para começar a usar o Device Co-op da Experience Cloud, entre em contato com o representante da Adobe.

Para habilitar seus aplicativos móveis para o Device Co-op da Experience Cloud, siga as etapas a seguir para os SDKs IOS da Experience Cloud.

>[!IMPORTANT]
>
>Esta funcionalidade exige a versão 4.8.5 ou posterior do SDK do iOS.

A partir do SDK versão 4.16.1, os membros do Device Co-op podem excluir os dados do dispositivo móvel do Device Co-op da Experience Cloud. Para obter mais informações, consulte [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md) e o `visitorAPI.js` método para [isCoopSafe](https://docs.adobe.com/content/help/pt-BR/id-service/using/id-service-api/configurations/coopsafe.html).

1. Implemente o SDK do Adobe Mobile.

   Para obter mais informações, consulte [Implementação principal e ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Habilitar sua Experience Cloud ID.

   Para obter mais informações, consulte [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).
1. Passe identidade autenticadas, como IDs do CRM ou emails com hash, usando um dos métodos de sincronização contidos aqui.

   Para obter mais informações, consulte [Métodos do Adobe Experience Platform Identity Service](/help/ios/marketing-cloud/mc-methods.md).

## sinalizador `coopUnsafe`

Veja a seguir algumas informações adicionais sobre o sinalizador `coopUnsafe`:

* Versão mínima do SDK: 4.16.1
* A propriedade booleana do objeto `marketingCloud` que, quando definido como `true`, causa a remoção do dispositivo do Device Co-op da Experience Cloud.
* O valor padrão é `false`.
* Essa configuração é usada **somente** para clientes provisionados do Device Co-op.

For Device Co-op members who require this value be set to `true`, you need to work with the Co-op team to request a blocklist flag on your Device Co-op account. Não há um caminho de autoatendimento para habilitar esses sinalizadores.

Lembre-se das seguintes informações:

* Quando `coopUnsafe` estiver definido como `true`, `coop_unsafe=1` sempre será anexado a ocorrências do Audience Manager e da ID do visitante.
* Se você habilitar o encaminhamento pelo lado do servidor do Analytics para o Audience Manager, você também verá `coop_unsafe=1` em ocorrências do Analytics.


