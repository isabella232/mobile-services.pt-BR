---
description: Estas informações ajudam a fazer uma viagem de ida e volta no link da campanha de aquisição herdada em um dispositivo Android.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: Estas informações ajudam a fazer uma viagem de ida e volta no link da campanha de aquisição herdada em um dispositivo Android.
seo-title: Teste da aquisição de legado
solution: Marketing Cloud, Analytics
title: Teste da aquisição de legado
topic: Desenvolvedor e implementação
uuid: bb 7 ace 96-68 eb -4 f 43-b 3 cf-af 80730 b 9 cee
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Testing legacy acquisition {#testing-legacy-acquisition}

Estas informações ajudam a fazer uma viagem de ida e volta no link da campanha de aquisição herdada em um dispositivo Android.

Se o aplicativo móvel ainda não estiver no Google Play, é possível selecionar qualquer aplicativo móvel como destino ao criar o link empresarial. Isso não afeta a capacidade de testar o link de aquisição, somente o aplicativo para o qual você é redirecionado pelo servidor de aquisição após clicar no link. Os parâmetros da cadeia de caracteres de consulta são passados para a Google Play store, que é passada para o aplicativo na instalação como parte de uma difusão de campanha. A viagem de ida e volta do teste de aquisição do aplicativo móvel requer uma simulação desse tipo de difusão.

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. Isso garante que as medições de ciclo de vida inicial associadas aos parâmetros de cadeia de caracteres de consulta da campanha sejam enviadas quando o aplicativo é inicializado pela primeira vez.

1. Na interface do usuário do Mobile Services, gere um URL de campanha de aquisição herdado.

   For more information, see [Use legacy Acquisition links](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).
1. Conecte o dispositivo a um computador, inicie o ADB Shell e inicie o aplicativo no dispositivo. 
1. Envie uma transmissão usando o formato a seguir:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. Complete as etapas a seguir:
   1. Substitua `com.example.adobetesttapp.com` pela entrada inversa do DNS do aplicativo.
   1. Atualize a referência do destinatário com a referência da localização de rastreamento no seu aplicativo.
   1. Replace values that are associated with `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign`, and so on, with appropriate values.

Se a transmissão for bem sucedida, é exibida uma resposta semelhante a apresentada abaixo:

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

Você visualizará também uma solicitação de imagem enviada aos servidores de coleção de dados da Adobe. Se o SDK aguardar a duração completa do tempo limite referencial, definido na etapa 1, com uma solicitação de imagem que não inclui parâmetros de campanha, a transmissão falhou.
