---
description: Esta é uma lista de métodos do Audience Manager fornecida pela biblioteca do Android.
keywords: android;library;mobile;sdk
seo-description: Esta é uma lista de métodos do Audience Manager fornecida pela biblioteca do Android.
seo-title: Métodos do Audience Manager
solution: Experience Cloud,Analytics
title: Métodos do Audience Manager
topic: Developer and implementation
uuid: 2f6e4664-1306-41d4-9fa7-e3a99f1df4ab
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 100%

---


# Métodos do Audience Manager{#audience-manager-methods}

Esta é uma lista de métodos do Audience Manager fornecida pela biblioteca do Android.

Atualmente, o SDK é compatível com várias soluções da Adobe Experience Cloud, como o Analytics, o Target, o Audience Manager e o Adobe Experience Platform Identity Service. Os métodos recebem o prefixo de acordo com a solução. Por exemplo, métodos da Experience Cloud ID recebem o prefixo `audience manager`.

Se o Audience Manager estiver configurado no arquivo JSON, um sinal que contém medições de ciclo de vida será enviado com a ocorrência de ciclo de vida.

* **getVisitorProfile**

   Retorna o perfil do visitante obtido recentemente e, se nenhum sinal for enviado, retorna `null`. O perfil do visitante é salvo em `SharedPreferences` para facilitar o acesso nas várias inicializações do aplicativo.

   * Esta é a sintaxe para este método:

      ```java
      public static HashMap<String, Object> getVisitorProfile(); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      HashMap<String, Object> visitorProfile = AudienceManager.getVisitorProfile(); 
      ```

* **getDpid**

   Retorna a DPID atual.

   * Esta é a sintaxe para este método:

      ```java
      public static void getDpid(); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      String dpid = AudienceManager.getDpid(); 
      ```

* **getDpuuid**

   Retorna a DPUUID atual.

   * Esta é a sintaxe para este método:

      ```java
      public static void getDpuuid(); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      String dpuuid = AudienceManager.getDpuuid(); 
      ```

* **setDpidAndDpuuid**

   Define a DPID e a DPUUID, e esses valores são enviados em cada sinal.

   Se o valor DPUUID passado para esse método contiver caracteres que não sejam seguros para URL, os clientes deverão codificar o parâmetro antes de passá-lo para o SDK.

   * Esta é a sintaxe para este método:

      ```java
      public static void setDpidAndDpuuid(String dpid, String dpuuid); 
      ```

   * Esta é a amostra de código para este método:

      ```java
      AudienceManager.setDpidAndDpuuid("myDpid", "myDpuuid"); 
      ```

* **signalWithData**

   Envia ao gerenciamento de público-alvo um sinal com características e obtém os segmentos correspondentes retornados em uma chamada de retorno de bloqueio.

   * Esta é a sintaxe para este método:

      ```java
      public static void signalWithData(Map<String, Object> data, AudienceManagerCallback<Map<String, Object>> callback);
      ```

   * Esta é a amostra de código para este método:

      ```java
      HashMap Traits = new HashMap<String, Object>();
      aamTraits.put("trait", "b");
      AudienceManager.signalWithData(aamTraits, new AudienceManager.AudienceManagerCallback<Map<String, Object>> () {
        @Override
         public void call(Map<String, Object> item) { 
              // segments come back here normally found in the segs object of your json 
         }
      });
      ```
