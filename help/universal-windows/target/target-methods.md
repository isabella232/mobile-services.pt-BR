---
description: Lista de métodos do Target fornecida pela biblioteca da plataforma Universal Windows.
seo-description: Lista de métodos do Target fornecida pela biblioteca da plataforma Universal Windows.
seo-title: Métodos do Target
solution: Marketing Cloud, Analytics
title: Métodos do Target
topic: Desenvolvedor e implementação
uuid: 2 ad 5953 b -7850-446 a -8053-b 3715 b 86329 b
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Métodos do Target {#target-methods}

Lista de métodos do Target fornecida pela biblioteca da plataforma Universal Windows.

O SDK atualmente é compatível com diversas Soluções da Adobe Experience Cloud, incluindo Analytics, Target e Audience Manager.

[As medições de ciclo de vida](/help/universal-windows/metrics.md) são enviadas como parâmetros para cada carregamento de mbox.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

## Referência de classe: TargetLocationRequest

## Propriedades

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

* **Loadrequest (winjs: Loadrequest)**

   Sends `request` to your configured Target server and returns the string value of the offer generated in a block `callback`.

   * Esta é a sintaxe para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * Esta é a amostra de código para este método:

      ```js
      var fADB = ADBMobile; 
       ADB.Target.loadRequest(heroBannerRequest).then(function(content){ 
          //do something with content returned from target server 
       });
      ```

* **Createrequest (winjs: Createrequest)**

   Cria um objeto `TargetLocationRequest` com os parâmetros fornecidos.

   * Esta é a sintaxe para este método:

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      var heroBannerRequest = ADB.Target.createRequest("heroBanner","default.png", null); 
      ```

* **Createorderconfirmrequest (winjs: Createorderconfirmrequest)**

   Cria um objeto `TargetLocationRequest` com os parâmetros fornecidos.

   * Esta é a sintaxe para este método:

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId,Platform::String ^orderTotal,Platform::String ^productPurchasedId,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * Esta é a amostra de código para este método:

      ```js
      varADB = ADBMobile;
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm","order","47.88","3722",null);
      ```

* **Clearcookies (winjs: Clearcookies)**

   Limpa os cookies do Target do aplicativo no dispositivo atual.

   * Esta é a sintaxe para este método:

      ```csharp
      static void ClearCookies();
      ```

   * Esta é a amostra de código para este método:

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **Getpcid (winjs: Getpcid)**

   Retorna o cookie da ID do PC do dispositivo atual.

   * Esta é a sintaxe para este método:

      ```csharp
      staticPlatform::String ^GetPcId();
      ```

   * Esta é a amostra de código para este método:

      ```js
      autopcId = ADBMobile.Target.getPcId();
      ```

* **Getsessionid (winjs: Getsessionid)**

   Retorna o cookie da ID da sessão do dispositivo atual.

   * Esta é a sintaxe para este método:

      ```csharp
      staticPlatform::String ^GetSessionId();
      ```

   * Esta é a amostra de código para este método:

      ```js
       autosessionId=ADBMobile.Target.getSessionId(); 
      ```

