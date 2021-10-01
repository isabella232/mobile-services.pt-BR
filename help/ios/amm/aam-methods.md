---
description: Esta é uma lista de métodos do Audience Manager fornecidos pela biblioteca do iOS.
solution: Experience Cloud,Analytics
title: Métodos do Audience Manager
topic-fix: Developer and implementation
uuid: 97658bd6-4c4f-4875-abe9-36dad4ec8bae
exl-id: b843a52f-2b83-4e19-9f43-895bd582d4ef
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 100%

---

# Métodos do Audience Manager {#audience-manager-methods}

Esta é uma lista de métodos do Audience Manager fornecidos pela biblioteca do iOS.

Atualmente, o SDK é compatível com várias soluções da Adobe Experience Cloud, como o Analytics, o Target, o Audience Manager e o Adobe Experience Platform Identity Service. Os métodos apresentam prefixos de acordo com a solução a qual estão associados. Logo, os métodos do Audience Manager apresentam o prefixo &quot;`audience`.&quot;

Se o Audience Manager estiver configurado em seu arquivo JSON, um sinal contendo as medições de ciclo de vida será enviado com `application:didFinishLaunchingWithOptions:`.

* **audienceVisitorProfile**

   Retorna o perfil do visitante obtido recentemente e, se nenhum sinal for enviado, retorna `null`. O perfil do visitante é salvo em `NSUserDefaults` para facilitar o acesso nas várias inicializações do aplicativo.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (NSDictionary *) audienceVisitorProfile;
      ```

   * Esta é a amostra de código para este menu:

      ```objective-c
      NSDictionary *profile = [ADBMobile audienceVisitorProfile]; 
      ```

* **audienceDpid**

   Retorna a DPID atual.

   * Esta é a sintaxe para este método:

      ```objective-c
      +(NSString *) audience Dpid;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSString *currentDpid = [ADBMobileaudience Dpid]; 
      ```

* **audienceDpuuid**

   Retorna a DPUUID atual.

   * Esta é a sintaxe para este método:

      ```objective-c
      +(NSString *) audienceDpuuid;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      NSString *currentDpuuid = [ADBMobileaudience Dpuuid]; 
      ```

* **audienceSetDpid:&#x200B;dpuuid:**

   Define a DPID e a DPUUID. Quando definidas, ambas serão anexadas a cada sinal.

   * A **ID do provedor de dados (DPID)** é a ID do parceiro de dados atribuída pelo Audience Manager.
   * O **identificador de usuário único (DPUUID) do provedor de dados** é o identificador exclusivo do provedor de dados para o usuário.

      >[!IMPORTANT]
      >
      >Antes da versão 4.13.x, a DPUUID não era codificada automaticamente. A partir da versão 4.13.x, o SDK primeiro descodifica o valor que foi transmitido e depois codifica novamente esse valor. Esse processo garante que o SDK não impeça a compatibilidade com versões anteriores.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) audienceSetDpid: (NSString*)   
                      dpiddpuuid:(NSString*)dpuuid;
      ```

   * Esta é a amostra de código para este método:

      ```objective-
      [ADBMobile audienceSetDpid:@"290"
                        dpuuid:@"99301393920493"];
      ```

* **audienceReset**

   Restaura o UUID do Audience Manager e elimina o perfil do visitante atual.

   * Esta é a sintaxe para este método:

      ```objective-c
      +(void) audienceReset;
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile audienceReset]; 
      ```

* **audienceSignalWithData::&#x200B;callback:**

   Envia ao Gerenciamento de público-alvo um sinal com características e obtém os segmentos correspondentes que são retornados em um bloco de retorno de chamada.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void) audienceSignalWithData:(NSDictionary*)data
                            callback:(void(^)(NSDictionary
      *response))callback; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile audienceSignalWithData:traits
                               callback:^(NSDictionary*response){
                                 //do something with returned segments
                               }];
      ```

## Exemplo

```objective-c
// setup your traits dictionary 
NSDictionary *traits = @{@"trait":@"b"}; 
// submit your signal and take action on results 
[ADBMobile audienceSignalWithData:traits  
                         callback:^(NSDictionary *response) { 
                             // do something with visitor segments here 
                             if ([response[@"gender"] isEqualToString:@"male"]) { 
                             // do something with gender  
                             } 
                         }];
```
