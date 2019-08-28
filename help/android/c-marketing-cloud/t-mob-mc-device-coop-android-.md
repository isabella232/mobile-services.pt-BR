---
description: Para começar a usar o Device Co-op da Experience Cloud, entre em contato com seu representante da Adobe.
seo-description: Para começar a usar o Device Co-op da Experience Cloud, entre em contato com seu representante da Adobe.
seo-title: Device Co-op da Experience Cloud
title: Device Co-op da Experience Cloud
uuid: 7 bb 8 a 19 c -4 b 80-4911-879 d-f 9941 baa 3 b 62
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Device Co-op da Experience Cloud {#experience-cloud-device-co-op}

Para começar a usar o Device Co-op da Experience Cloud, entre em contato com seu representante da Adobe.

Para ativar os aplicativos móveis no Device Co-op da Experience Cloud, complete as etapas a seguir dos Android SDKs da Experience Cloud:

>[!IMPORTANT]
>
>Essa funcionalidade requer o Android SDK versão 4.8.3 ou posterior.

A partir da versão 4.16.1 do SDK, membros do Device Co-op podem remover seus dados de dispositivo móvel do Device Co-op da Experience Cloud. Para obter mais informações, consulte [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md) e o método `visitorAPI.js` para [isCoopSafe](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-coopsafe.html).

1. Implemente o SDK do Adobe Mobile.

   Para obter mais informações, consulte [Implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).
1. Habilitar sua Experience Cloud ID.

   For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).
1. Passe identidades autenticadas, como IDs do CRM ou emails com hash, ao usar um dos métodos de sincronização contidos aqui.

   Para obter mais informações, consulte [Métodos de serviço de identidade da Adobe Experience Platform](/help/android/c-marketing-cloud/mc-methods.md).

## `coopUnsafe` sinalizador

Aqui estão algumas informações adicionais sobre o sinalizador `coopUnsafe`:

* Versão mínima do SDK: 4.16.1
* The Boolean property of the `marketingCloud` object that, when set to `true`, causes the device to be opted-out of the Experience Cloud's Device Co-Op.
* O valor padrão é `false`.
* Essa configuração é usada **somente** para clientes provisionados do Device Co-op.

Para membros do Device Co-op que requerem que esse valor seja definido como `true`, é necessário trabalhar com a equipe do Co-op para solicitar um sinalizador de lista de bloqueios em sua conta do Device Co-op. Não há um caminho de autoatendimento para habilitar esses sinalizadores.

Lembre-se das seguintes informações:

* When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
* If you enable Analytics server-side forwarding to Audience Manager, you will also see `coop_unsafe=1` Analytics hits.