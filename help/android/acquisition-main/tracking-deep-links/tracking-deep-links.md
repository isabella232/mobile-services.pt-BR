---
description: É possível usar essas informações para rastrear deep links e deep links adiados nos aplicativos móveis com o Adobe Mobile Android SDK.
keywords: android;biblioteca;móvel;sdk
seo-description: É possível usar essas informações para rastrear deep links e deep links adiados nos aplicativos móveis com o Adobe Mobile Android SDK.
seo-title: Rastreamento de deep links no Adobe Mobile Services
solution: Experience Cloud,Analytics
title: Rastreamento de deep links
topic-fix: Developer and implementation
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
exl-id: 4f59b77d-3cac-4853-bb6b-50a403036771
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 100%

---

# Rastreamento de deep links

É possível usar essas informações para rastrear deep links e deep links adiados nos aplicativos móveis com o Adobe Mobile Android SDK.

## Rastreamento de deep links

1. Adicione o SDK ao seu projeto e implemente as medições de ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto IntelliJ IDEA ou Eclipse* em [Implementação principal e Ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Registre o aplicativo para manipular URLs.

   Para obter mais informações, consulte as [URLs](https://developer.android.com/training/basics/intents/filters.html).
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

O SDK do Adobe Mobile pode analisar pares de dados de chaves e valores adicionados a qualquer deep link ou link universal, desde que o link contenha uma chave com um rótulo `a.deeplink.id` e um valor não-nulo correspondente gerado pelo usuário. Todos os pares de dados de chaves e valores adicionados ao link serão analisados, anexados a uma ocorrência de ciclo de vida e enviados ao Adobe Analytics, desde que o link contenha a chave e o valor para `a.deeplink.id`.

Além disso, também é possível anexar uma ou mais das seguintes chaves reservadas (com valores gerados pelo usuário) ao deep link ou ao link universal:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Essas chaves são variáveis pré-mapeadas para relatórios no Adobe Analytics. Para obter mais informações sobre regras de mapeamento e processamento, consulte [Regras de processamento e dados de contexto](https://docs.adobe.com/content/help/pt-BR/analytics/admin/admin-tools/processing-rules/processing-rules.html).

## Rastrear deep links adiados (para usar com links de marketing)

Com um deep link adiado, o SDK da Adobe abrirá um novo Propósito com o deep link como os dados de intenção. Esse processo é manipulado como um deep link externo usando o código acima.

## Informações públicas do deep link {#section_1815396353614DA8A63D8D92112217E7}

### Constantes

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```
