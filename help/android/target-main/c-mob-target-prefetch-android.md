---
description: O recurso de busca prévia do Adobe Target usa o SDK móvel do Android para buscar conteúdo de oferta a menor quantidade de vezes possível, armazenando as respostas do servidor em cache.
seo-description: O recurso de busca prévia do Adobe Target usa o SDK móvel do Android para buscar conteúdo de oferta a menor quantidade de vezes possível, armazenando as respostas do servidor em cache.
seo-title: Usar a busca prévia para encontrar conteúdos de oferta no Android
title: Usar a busca prévia para encontrar conteúdos de oferta no Android
uuid: 063451b8-e191-4d58-8ed8-1723e310ad1a
translation-type: tm+mt
source-git-commit: fa7375ac8a1345d81748bcf635791c46d3943fed

---


# Usar a busca prévia para encontrar conteúdos em oferta no Android {#prefetch-offer-content-in-android}

O recurso de busca prévia do Adobe Target usa o SDK móvel do Android para buscar conteúdo de oferta a menor quantidade de vezes possível, armazenando as respostas do servidor em cache.

>[!IMPORTANT]
>
>Prefetch functionality in the Mobile SDKs for Android is not supported for Auto Target, Auto Allocate, and Automated Personalization activity types in Adobe Target.

Esse processo reduz o tempo de carregamento, previne várias chamadas de rede e permite que o Adobe Target seja notificado sobre que mbox foi visitada pelo usuário do aplicativo móvel. Todo o conteúdo será recuperado e armazenado em cache durante a chamada da busca prévia, e esse conteúdo será recuperado do cache em todas as chamadas futuras que contenham conteúdo armazenado em cache para o nome da mbox especificado.

O conteúdo da busca prévia não persiste entre inicializações. The prefetch content is cached as long as the application lives or until the `clearPrefetchCache()` method is called.

>[!IMPORTANT]
>
>Target prefetch APIs have been available since SDK version 4.14.0. For more information about parameter limitations, see [Batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters).

No SDK de versão 4.14 ou posterior, se especificado, a `environmentId``ADBMobileConfig.json` é extraída do arquivo ao iniciar uma chamada v2 batch mbox TnT. Caso nenhuma `environmentId` esteja especificada nesse arquivo, nenhum parâmetro de ambiente é enviado pela chamada TNT batch mbox, e a oferta é entregue ao ambiente padrão.

Por exemplo:

```java
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Pre-fetch methods {#section_05967F1F3A554B0FBC2C08A954554BDE}

Estes são os métodos que você pode usar para realizar uma busca prévia no Android:

* **prefetchContent**

   Envia uma solicitação de busca prévia com uma matriz de localizações para o servidor do Target configurado e retorna o status da solicitação na chamada de retorno fornecida.

   * Esta é a sintaxe para este método:

      ```java
      public static void prefetchContent(
      final List<TargetPrefetchObject> targetPrefetchArray,
      final Map<String, Object> profileParameters,
      final TargetCallback<Boolean> callback)
      ```

   * Here are the parameters for this method:

      * **targetPrefetchArray**

         Matriz de `TargetPrefetchObjects` que contém o nome e os mboxParameters para cada localização do Target na qual se deve realizar uma busca prévia.

      * **profileParameters**

         Contém as chaves e os valores dos parâmetros de perfil a ser usados com cada localização de busca prévia nesta solicitação.

      * **callback**

         Invocado quando a busca prévia está concluída. Returns `true` if the prefetch was successful and `false` if the prefetch was unsuccesful.

* **loadRequests**

   Executa uma solicitação em lote em várias localizações de mbox especificadas no vetor de solicitações.  Cada objeto na matriz contém uma função de chamada de retorno, que será invocada quando o conteúdo estiver disponível na localização da mbox fornecida.

   >[!IMPORTANT]
   >
   >Se o conteúdo dos locais solicitados já estiver armazenado em cache, ele será retornado imediatamente na chamada de retorno fornecida. Caso contrário, o SDK enviará uma solicitação de rede para que os servidores do Target recuperem o conteúdo.

   * Esta é a sintaxe para este método:

      ```java
      public static void loadRequests( final List<TargetRequestObject> requestArray,  final Map<String, Object> profileParameters)
      ```

   * Here are the parameters for this method:

      * **requestArray**

         Matriz de `TargetRequestObjects` que contém o nome, o conteúdo padrão, os parâmetros e a função de chamada de retorno para cada localização a ser recuperada.

      * **profileParameters**

         Contém as chaves e os valores dos parâmetros de perfil a ser usados com cada localização de busca prévia nesta solicitação.

* **clearPrefetchCache**

   Limpa os dados armazenados em cache pela busca prévia do Target.

   * Esta é a sintaxe para este método:

      ```java
      public static void clearPrefetchCache();
      ```

   * There are no parameters for this method.

* **createTargetRequestObject**

   Cria e retorna uma instância de `TargetRequestObject` com os dados fornecidos.

   * Esta é a sintaxe para este método:

      ```java
      public static TargetPrefetchObject createTargetRequestObject( 
      final String mboxName,
      final String defaultContent, 
      final Map<String, Object> mboxParams, 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams, 
      final Target.TargetCallback<String> callback)
      ```

* **createTargetPrefetchObject**

   Cria e retorna uma instância de TargetPrefetchObject com os dados fornecidos.

   * Esta é a sintaxe para este método:

      ```java
      public static TargetPrefetchObject createTargetPrefetchObject( 
      final String mboxName, 
      final Map<String, Object> mboxParams) 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams)
      ```

## Public classes {#section_A273E53F069E4327BBC8CE4910B37888}

Estas são as classes públicas que oferecem suporte para busca prévia no Android:

### Class reference: TargetPrefetchObject

Encapsula o nome e os parâmetros da mbox usados na busca prévia da mbox.

* **`name`**

   Nome da localização onde será realizada a busca prévia.
   * **Tipo**: String

* `mboxParameters`

   Coleção de pares de chave-valor que serão anexados como `mboxParameters` nessa solicitação do `TargetPrefetchObject`.
   * **Type**: Map`<String, Object>`

* **`orderParameters`**

   Coleção de pares de chave-valor que serão anexados a mbox atual no nó ordem.
   * **Type: Map**`<String, Object>`

* **`productParameters`**

   Coleção de pares de chave-valor que serão anexados a mbox atual no nó produtos.

   * **Type: Map**`<String, Object>`


### Class reference: TargetRequestObject

Essa classe encapsula o nome da mbox, o conteúdo padrão, os parâmetros da mbox e a função de retorno usada nas solicitações de localização do Target.

* **`mboxName`**

   Nome da localização solicitada.

   * **Tipo**: String

* **`mboxParameters`**

   Coleção de pares de chave-valor que serão anexados como `mboxParameters` nesse  `TargetRequestObject`.

   * **Tipo: Map`<String, Object>`**

* **`orderParameters`**

   Coleção de pares de chave-valor que serão anexados a mbox atual no nó ordem.

   * **Type: Map**`<String, Object>`

* **`productParameters`**

   Coleção de pares de chave-valor que serão anexados a mbox atual no nó produtos.

   * **Type: Map**`<String, Object>`

* **`defaultContent`**

   Valor da string retornada pela função de retorno se o SDK não for capaz de recuperar o conteúdo dos servidores do Target.

   * **Tipo**: String

* **`callback`**

   Ponteiro para a função a ser chamada quando o conteúdo de um dado `TargetRequestObject` estiver disponível.

   * **Type: Target.TargetCallback**`<String>`


## Code sample {#section_BF7F49763D254371B4656E17953D520C}

Este é um exemplo de como fazer uma busca prévia de conteúdo por meio dos SDKs do Android:

```java
// When your app launches, prefetch the content for a list of locations. 
// Define the list of mboxes that you want to prefetch. 
List<TargetPrefetchObject> prefetchMboxesList = new ArrayList<>(); 
  
Map<String, Object> mboxParameters1 = new HashMap<>(); 
mboxParameters1.put("status", "platinum"); 
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName1", mboxParameters1));

Map<String, Object> mboxParameters2 = new HashMap<>(); 
mboxParameters2.put("userType", "paid"); 
 
List<String> purchasedIds = new ArrayList<String>(); 
purchasedIds.add("34"); 
purchasedIds.add("125");  
Map<String, Object> orderParameters2 = new HashMap<>(); 
orderParameters2.put("id", "ADCKKIM"); 
orderParameters2.put("total", "344.30"); 
orderParameters2.put("purchasedProductIds",  purchasedIds); 
  
Map<String, Object> productParameters2 = new HashMap<>(); 
productParameters2.put("id", "24D3412"); 
productParameters2.put("categoryId","Books"); 
  
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName2", mboxParameters2, orderParameters2, productParameters2));

// Define the profile parameters map. 
Map<String, Object> profileParameters = new HashMap<>(); 
profileParameters.put("ageGroup", "20-32");

// Define the target callback for the prefetch call status. 
Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() { 
    @Override 
    public void call(final Boolean status) { 
        // check the returned status for the prefetch call 
    }};

// Call the prefetchContent API. 
Target.prefetchContent(prefetchMboxesList, profileParameters, prefetchStatusCallback);

// When the content is required, you can initiate the locations request. 
// Define the list of target request objects. 
List<TargetRequestObject> locationRequests = new ArrayList<>(); 
  
Target.TargetCallback<String> callback1 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName1. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName1", "defaultContent1", mboxParameters1, callback1));

Target.TargetCallback<String> callback2 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName2. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName2", "defaultContent2", mboxParameters2, orderParameters2, productParameters2, callback2)); 
  
// Call the loadRequests API. 
Target.loadRequests(locationRequests, profileParameters); 
```

## Informações adicionais {#section_A454BAD1CD49423E86C71BAEE06125FD}

Estas são algumas informações adicionais sobre essas amostras:

* `ProductParameters` permite somente as seguintes chaves:

   * `id`
   * `categoryId`

* `OrderParameters` permite somente as seguintes chaves:

   * `id`
   * `total`
   * `purchasedProductIds`

* `purchasedProducts` aceita uma ArrayList de strings.
