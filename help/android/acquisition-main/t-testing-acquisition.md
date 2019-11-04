---
description: Estas informações ajudam a fazer uma viagem de ida e volta no link da campanha de aquisição herdada em um dispositivo Android.
keywords: android;biblioteca;móvel;sdk
seo-description: Estas informações ajudam a fazer uma viagem de ida e volta no link da campanha de aquisição herdada em um dispositivo Android.
seo-title: Teste da aquisição de legado
solution: Experience Cloud,Analytics
title: Teste da aquisição de legado
topic: Desenvolvedor e implementação
uuid: bb7ace96-68eb-4f43-b3cf-af80730b9cee
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Teste de aquisição de legado {#testing-legacy-acquisition}

Estas informações ajudam a fazer uma viagem de ida e volta no link da campanha de aquisição herdada em um dispositivo Android.

Se o aplicativo móvel ainda não estiver no Google Play, é possível selecionar qualquer aplicativo móvel como destino ao criar o link empresarial. Isso não afeta a capacidade de testar o link de aquisição, somente o aplicativo para o qual você é redirecionado pelo servidor de aquisição após clicar no link. Os parâmetros da cadeia de caracteres de consulta são passados para a Google Play store, que é passada para o aplicativo na instalação como parte de uma difusão de campanha. A viagem de ida e volta do teste de aquisição do aplicativo móvel requer uma simulação desse tipo de difusão.

O aplicativo deve estar recém-instalado ou ter os dados limpos em [!UICONTROL **Configurações**] sempre que um teste for executado. Isso garante que as medições de ciclo de vida inicial associadas aos parâmetros de cadeia de caracteres de consulta da campanha sejam enviadas quando o aplicativo é inicializado pela primeira vez.

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

Se a transmissão for bem sucedida, é exibida uma resposta semelhante a apresentada abaixo:

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

Você visualizará também uma solicitação de imagem enviada aos servidores de coleção de dados da Adobe. Se o SDK aguardar a duração completa do tempo limite referencial, definido na etapa 1, com uma solicitação de imagem que não inclui parâmetros de campanha, a transmissão falhou.
