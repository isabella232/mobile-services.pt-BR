---
description: Para começar a usar o Device Co-op da Experience Cloud, entre em contato com o representante da Adobe.
seo-description: Para começar a usar o Device Co-op da Experience Cloud, entre em contato com o representante da Adobe.
seo-title: Device Co-op da Experience Cloud
title: Device Co-op da Experience Cloud
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: tm+mt
source-git-commit: 86ba045b44bf6553e80727c0d61ccdd9a552d16c
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 100%

---


# Device Co-op da Experience Cloud {#experience-cloud-device-co-op}

Para começar a usar o Device Co-op da Experience Cloud, entre em contato com o representante da Adobe.

Para habilitar seus aplicativos móveis para o Device Co-op da Experience Cloud, siga as etapas a seguir para os SDKs Android da Experience Cloud:

>[!IMPORTANT]
>
>Esta funcionalidade exige a versão 4.8.3 ou posterior do SDK do Android.

A partir do SDK versão 4.16.1, os membros do Device Co-op podem excluir os dados do dispositivo móvel do Device Co-op da Experience Cloud. Para obter mais informações, consulte [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md) e o `visitorAPI.js` método para [isCoopSafe](https://docs.adobe.com/content/help/pt-BR/id-service/using/id-service-api/configurations/coopsafe.html).

1. Implemente o SDK do Adobe Mobile.

   Para obter mais informações, consulte [Implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).
1. Habilitar sua Experience Cloud ID.

   Para obter mais informações, consulte [Configuração da Experience Cloud ID](/help/android/c-marketing-cloud/mcvid.md).
1. Passe identidades autenticadas, como IDs do CRM ou emails com hash, ao usar um dos métodos de sincronização contidos aqui.

   Para obter mais informações, consulte [Métodos do Adobe Experience Platform Identity Service](/help/android/c-marketing-cloud/mc-methods.md).

## sinalizador `coopUnsafe`

Aqui estão algumas informações adicionais sobre o sinalizador `coopUnsafe`:

* Versão mínima do SDK: 4.16.1
* A propriedade booleana do objeto `marketingCloud` que, quando definido como `true`, causa a remoção do dispositivo do Device Co-op da Experience Cloud.
* O valor padrão é `false`.
* Essa configuração é usada **somente** para clientes provisionados do Device Co-op.

Para membros do Device Co-op que requerem que esse valor seja definido como `true`, é necessário trabalhar com a equipe do Co-op para solicitar um sinalizador de lista de bloqueios em sua conta do Device Co-op. Não há um caminho de autoatendimento para habilitar esses sinalizadores.

Lembre-se das seguintes informações:

* Quando `coopUnsafe` estiver definido como `true`, `coop_unsafe=1` sempre será anexado a ocorrências do Audience Manager e da ID do visitante.
* Se você habilitar o encaminhamento pelo lado do servidor do Analytics para o Audience Manager, você também verá `coop_unsafe=1` em ocorrências do Analytics.