---
description: Lista de métodos do Audience Manager fornecida pela biblioteca da plataforma Universal Windows.
solution: Experience Cloud,Analytics
title: Métodos do Audience Manager
topic-fix: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
exl-id: a7b4001d-d90f-4a8a-a801-d66e56ea43b5
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 44%

---

# Métodos do Audience Manager{#audience-manager-methods}

Lista de métodos do Audience Manager fornecida pela biblioteca da plataforma Universal Windows.

Atualmente, o SDK é compatível com várias soluções da Adobe Experience Cloud, incluindo o Analytics, o Target e o Audience Manager. Os métodos recebem o prefixo de acordo com a solução. Métodos Audience Manager recebem o prefixo `AudienceManager`.

>[!TIP]
>
>Ao consumir métodos `winmd` do winJS (JavaScript), todos os métodos passam a ter a primeira letra em minúsculas automaticamente.

Se o audience manager estiver configurado em seu arquivo JSON, um sinal contendo as medições de ciclo de vida será enviado com a ocorrência de ciclo de vida.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Retorna o perfil do visitante obtido recentemente. Retorna `null` se nenhum sinal tiver sido enviado. O perfil do visitante é salvo em `SharedPreferences` para facilitar o acesso em várias inicializações do aplicativo.

   * Esta é a sintaxe para este método:

      ```csharp
      static Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^GetVisitorProfile();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **GetDpid (winJS: getDpid)**

   Retorna a DPID atual.

   * Esta é a sintaxe para este método:

      ```csharp
      static Platform::String ^GetDpid();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      var dpid = ADB.AudienceManager.getDpid(); 
      ```

* **GetDpuuid (winJS: getDpuuid)**

   Retorna a DPUUID atual.

   * Esta é a sintaxe para este método:

      ```csharp
      static Platform::String ^GetDpuuid();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile; 
      var dpuuid = ADB.AudienceManager.getDpuuid();
      ```

* **SetDpidAndDpuuid (winJS: setDpidAndDpuuid)**

   Define a DPID e a DPUUID. Se DPID e DPUUID estiverem definidas, elas serão enviadas com cada sinal.

   * Esta é a sintaxe para este método:

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid);
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **SignalWithData (winJS: signalWithData)**

   Envia ao gerenciamento de público-alvo um sinal com características e obtém os segmentos correspondentes retornados em uma chamada de retorno de bloqueio.

   * Esta é a sintaxe para este método:

      ```csharp
      static 
      Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^> ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object> ^data);
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile;
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b";
      ADB.AudienceManager.signalWithData(traits).then(function (visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      });
      ```
