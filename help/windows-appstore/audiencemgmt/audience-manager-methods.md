---
description: Lista de métodos Audience Manager fornecidos pela biblioteca da loja de aplicativos universal do Windows 8.1.
seo-description: Lista de métodos Audience Manager fornecidos pela biblioteca da loja de aplicativos universal do Windows 8.1.
seo-title: Métodos do Audience Manager
solution: Marketing Cloud,Analytics
title: Métodos do Audience Manager
topic: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 45%

---


# Métodos do Audience Manager {#audience-manager-methods}

Lista de métodos Audience Manager fornecidos pela biblioteca da loja de aplicativos universal do Windows 8.1.

O SDK suporta atualmente várias Soluções Adobe Experience Cloud, incluindo Analytics, Público alvo e Audience Manager. Os métodos apresentam prefixos de acordo com a solução. Métodos Audience Manager recebem o prefixo &quot;AudienceManager&quot;.

>[!NOTE]
>
>Quando você consome métodos winmd de winJS (JavaScript), todos os métodos têm automaticamente sua primeira letra em minúsculas.

Se o gerenciador de audiências estiver configurado no arquivo JSON, um sinal contendo as medições de ciclo de vida será enviado com a ocorrência de ciclo de vida.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Retorna o perfil do visitante obtido recentemente. Returns `null` if no signal has been submitted yet. Visitor profile is saved in `SharedPreferences` for easy access across multiple launches of your app.

   * Esta é a sintaxe para este método:

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
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

   Envia sinal de Audience Manager com características e obtém os segmentos correspondentes retornados em uma chamada de bloqueio.

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

