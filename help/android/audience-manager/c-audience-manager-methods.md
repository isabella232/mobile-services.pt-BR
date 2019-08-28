---
description: Esta é uma lista de métodos do Audience Manager fornecida pela biblioteca do Android.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: Esta é uma lista de métodos do Audience Manager fornecida pela biblioteca do Android.
seo-title: Métodos do Audience Manager
solution: Marketing Cloud, Analytics
title: Métodos do Audience Manager
topic: Desenvolvedor e implementação
uuid: 2 f 6 e 4664-1306-41 d 4-9 fa 7-e 3 a 99 f 1 df 4 ab
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Audience Manager methods{#audience-manager-methods}

Esta é uma lista de métodos do Audience Manager fornecida pela biblioteca do Android.

O SDK suporta atualmente várias Soluções da Adobe Experience Cloud, incluindo Analytics, Target, Audience Manager e Adobe Experience Platform Identity Service. Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `audience manager`.

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

   Se o valor DPUUID que é passado para esse método contiver caracteres que não são seguros para URL, os clientes devem codificar o parâmetro antes de passá-lo para o SDK.

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
