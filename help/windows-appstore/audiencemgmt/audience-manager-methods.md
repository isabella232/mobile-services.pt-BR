---
description: Lista de métodos do Audience Manager fornecidos pela biblioteca da loja de aplicativos universal do Windows 8.1.
seo-description: Lista de métodos do Audience Manager fornecidos pela biblioteca da loja de aplicativos universal do Windows 8.1.
seo-title: Métodos do Audience Manager
solution: Marketing Cloud, Analytics
title: Métodos do Audience Manager
topic: Desenvolvedor e implementação
uuid: e 39 c 9 c 3 e-fd 53-4 b 46-8 fff -88101 a 064 a 9 c
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Audience Manager methods {#audience-manager-methods}

Lista de métodos do Audience Manager fornecidos pela biblioteca da loja de aplicativos universal do Windows 8.1.

O SDK atualmente é compatível com diversas Soluções da Adobe Experience Cloud, incluindo Analytics, Target e Audience Manager. Os métodos apresentam prefixos de acordo com a solução. Métodos do Audience Manager recebem o prefixo “AudienceManager”.

>[!NOTE]
>
>Quando você usa métodos winmd de winjs (javascript), todos os métodos têm a primeira letra em minúsculas automaticamente.

Se o Audience Manager estiver configurado no arquivo JSON, um sinal que contém as métricas de ciclo de vida será enviado com a ocorrência de ciclo de vida.

* **Getvisitorprofile (winjs: Getvisitorprofile)**

   Retorna o perfil do visitante obtido recentemente. Retorna `null` se nenhum sinal tiver sido enviado. O perfil do visitante é salvo em `SharedPreferences` para facilitar o acesso em vários lançamentos do aplicativo.

   * Esta é a sintaxe para este método:

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **Getdpid (winjs: Getdpid)**

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

* **Getdpuuid (winjs: Getdpuuid)**

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

* **Setdpidanddpuuid (winjs: Setdpidanddpuuid)**

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

* **Signalwithdata (winjs: Signalwithdata)**

   Envia ao Audience Manager um sinal com características e obtém os segmentos correspondentes retornados em uma chamada de bloqueio.

   * Esta é a sintaxe para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> > ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^data);
      ```

   * Esta é a amostra de código para este método:

      ```js
      var ADB = ADBMobile; 
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b"; 
      ADB.AudienceManager.signalWithData(traits).then(function(visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      ```

