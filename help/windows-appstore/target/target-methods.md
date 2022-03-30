---
description: Lista de métodos do Target fornecida pela biblioteca Universal App Store do Windows 8.1.
solution: Experience Cloud Services,Analytics
title: Métodos do Target
topic-fix: Developer and implementation
uuid: 8c35b31c-c70b-4dba-8759-173342a301e9
exl-id: 2db9f594-01e7-4ca8-a90e-9d12278350d0
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 43%

---

# Métodos do Target {#target-methods}

Lista de métodos do Target fornecida pela biblioteca Universal App Store do Windows 8.1.

Atualmente, o SDK é compatível com várias soluções da Adobe Experience Cloud, incluindo o Analytics, o Target e o Audience Manager. Os métodos apresentam prefixos de acordo com a solução. Métodos do Analytics recebem o prefixo &quot;Target&quot;.

[Medições de ciclo de vida](/help/windows-appstore/metrics.md) são enviadas como parâmetros para cada carregamento de mbox.

>[!TIP]
>
>Ao consumir `winmd` métodos do winJS (JavaScript), todos os métodos passam a ter a primeira letra em minúsculas automaticamente.

## Referência de classe: TargetLocationRequest

### Propriedades

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## Constantes da cadeia de caracteres

Estas informações ajudam a definir chaves para parâmetros personalizados.

```
static property Platform::String ^TARGET_PARAMETER_ORDER_ID { 
  Platform::String ^get() { return L"orderId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_ORDER_TOTAL { 
  Platform::String ^get() { return L"orderTotal"; } 
} 
static property Platform::String ^TARGET_PARAMETER_PRODUCT_PURCHASE_ID { 
  Platform::String ^get() { return L"productPurchasedId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_CATEGORY_ID { 
  Platform::String ^get() { return L"categoryId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_3RDPARTY_ID { 
  Platform::String ^get() { return L"mbox3rdPartyId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PAGE_VALUE { 
  Platform::String ^get() { return L"mboxPageValue"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PC { 
  Platform::String ^get() { return L"mboxPC"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_SESSION_ID { 
  Platform::String ^get() { return L"mboxSession"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_HOST { 
  Platform::String ^get() { return L"mboxHost"; } 
}
```

* **LoadRequest (winJS: loadRequest)**

   Envia `request` ao servidor do Target configurado e retorna o valor da cadeia de caracteres da oferta gerada em um bloco `callback`.

   * Esta é a sintaxe para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile; 
      ADB.Target.loadRequest(heroBannerRequest).then(function(content) { 
      // do something with content returned from target server 
      });
      ```

* **CreateRequest (winJS: createRequest)**

   Cria um `TargetLocationRequest` com os parâmetros fornecidos.

   * Esta é a sintaxe para este método:

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile; 
      var heroBannerRequest = ADB.Target.createRequest("heroBanner", "default.png", null); 
      ```

* **CreateOrder &#x200B; ConfirmRequest (winJS: createOrder &#x200B; ConfirmRequest)**

   Cria um `TargetLocationRequest` com os parâmetros fornecidos.

   * Esta é a sintaxe para este método:

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId, Platform::String ^orderTotal, Platform::String ^productPurchasedId, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^parameters); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile; 
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null); 
      ```

* **ClearCookies (winJS: clearCookies)**

   Apaga os cookies do Target para o aplicativo no dispositivo atual.

   * Esta é a sintaxe para este método:

      ```csharp
      static void ClearCookies(); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId (winJS: getPcId)**

   Retorna o cookie da ID do PC do dispositivo atual.

   * Esta é a sintaxe para este método:

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * Esta é a amostra de código para este método:

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **GetSessionId (winJS: getSessionId)**

   Retorna o cookie da ID da sessão do dispositivo atual.

   * Esta é a sintaxe para este método:

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```
