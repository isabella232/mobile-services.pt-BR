---
description: É possível usar essas informações para rastrear deep links e deep links adiados nos aplicativos móveis com o Adobe Mobile Android SDK.
keywords: android;biblioteca;móvel;sdk
seo-description: É possível usar essas informações para rastrear deep links e deep links adiados nos aplicativos móveis com o Adobe Mobile Android SDK.
seo-title: Rastreamento de deep links no Adobe Mobile Services
solution: Marketing Cloud,Analytics
title: Rastreamento de deep links
topic: Desenvolvedor e implementação
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Tracking deep links {#tracking-deep-links}

É possível usar essas informações para rastrear deep links e deep links adiados nos aplicativos móveis com o Adobe Mobile Android SDK.

## Rastrear links profundos

1. Adicione o SDK ao seu projeto e implemente as medições de ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto* IntelliJ IDEA ou Eclipse na implementação e ciclo de vida [principais](/help/android/getting-started/dev-qs.md).

1. Registre o aplicativo para manipular URLs.

   Para obter mais informações, consulte [URLs](https://developer.android.com/training/basics/intents/filters.html).
1. Passe a atividade com intenção de deep link para o Adobe SDK com `collectLifecycleData`.

   Este é um exemplo de rastreamento de deep link:

   ```java
   public class ParseDeepLinkActivity extends Activity { 
       @Override 
       protected void onCreate(Bundle savedInstanceState) { 
           super.onCreate(savedInstanceState); 
   
           Config.collectLifecycleData(this); 
           ... 
       } 
   }
   ```

The Adobe Mobile] SDK can parse key and value pairs of data that is appended to any Deep or Universal Link as long as the link contains a key with the `a.deeplink.id` label and a corresponding non-null and user-generated value. All key and value pairs of data that are appended to the link will be parsed, attached to a lifecycle hit, and sent to Adobe Analytics] as long as the link contains the `a.deeplink.id` key and value.

Additionally, you might append one or more of the following reserved keys (with user-generated values) to the deep or Universal Link:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Essas chaves são variáveis pré-mapeadas para relatórios no Adobe Analytics. Para obter mais informações sobre regras de mapeamento e processamento, consulte [Regras de processamento e Dados de contexto](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

## Tracking deferred deep links (for use with Marketing Links)

No caso de um deep link adiado, o Adobe SDK abrirá uma nova Intenção com o deep link como os dados de intenção. Esse processo é executado como um deep link externo, usando o código acima.

## Deep link public information {#section_1815396353614DA8A63D8D92112217E7}

### Constantes

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```

