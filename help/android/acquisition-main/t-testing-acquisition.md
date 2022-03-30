---
description: Estas informações ajudam a fazer uma viagem de ida e volta no link da campanha de aquisição herdada em um dispositivo Android.
keywords: android;biblioteca;móvel;sdk
solution: Experience Cloud Services,Analytics
title: Teste de aquisição de legado
topic-fix: Developer and implementation
uuid: bb7ace96-68eb-4f43-b3cf-af80730b9cee
exl-id: 43e3b24e-e8bc-407c-b788-5ab85e459a90
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 100%

---

# Teste de aquisição de legado {#testing-legacy-acquisition}

Estas informações ajudam a fazer uma viagem de ida e volta no link da campanha de aquisição herdada em um dispositivo Android.

Se o aplicativo móvel ainda não estiver na Google Play, você pode selecionar qualquer aplicativo móvel como destino ao criar o link da campanha. Essa ação não afeta a capacidade de testar o link de aquisição, afeta somente o aplicativo para o qual você é redirecionado pelo servidor de aquisição após clicar no link. Os parâmetros da string de query são passados para a Google Play store, que são passados para o aplicativo na instalação como parte de uma transmissão de campanha. O teste de aquisição de aplicativo móvel de ida e volta requer a simulação desse tipo de transmissão.

O aplicativo deve estar recém-instalado ou ter os dados limpos em **[!UICONTROL Configurações]** sempre que um teste for executado. Isso garante que as medições de ciclo de vida inicial associadas aos parâmetros de cadeia de caracteres de consulta da campanha sejam enviadas quando o aplicativo é inicializado pela primeira vez.

1. Na interface do usuário do Mobile Services, gere um URL de campanha de aquisição herdado.

   Para obter mais informações, consulte [Usar links de aquisição de legado](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).
1. Conecte o dispositivo a um computador, inicie o ADB Shell e inicie o aplicativo no dispositivo.
1. Enviar uma transmissão usando o formato a seguir:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. Complete as etapas a seguir:
   1. Substitua `com.example.adobetesttapp.com` pela entrada inversa do DNS do aplicativo.
   1. Atualize a referência do destinatário com a referência da localização de rastreamento no seu aplicativo.
   1. Substitua os valores associados a `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign`, e outros, pelos valores adequados.

Se a transmissão for bem-sucedida, uma resposta semelhante à abaixo será exibida:

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

Você também verá uma solicitação de imagem enviada para os servidores de coleta de dados Adobe. Se o SDK aguardar a duração completa do tempo limite do referenciador, definido na etapa 1, com uma solicitação de imagem que não inclui parâmetros de campanha, a transmissão falhou.
