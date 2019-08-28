---
description: Esta é uma lista de métodos do Audience Manager fornecidos pela biblioteca do iOS.
seo-description: Esta é uma lista de métodos do Audience Manager fornecidos pela biblioteca do iOS.
seo-title: Métodos do Audience Manager
solution: Marketing Cloud, Analytics
title: Métodos do Audience Manager
topic: Desenvolvedor e implementação
uuid: 97658 bd 6-4 c 4 f -4875-abe 9-36 dad 4 ec 8 bae
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Audience Manager methods {#audience-manager-methods}

Esta é uma lista de métodos do Audience Manager fornecidos pela biblioteca do iOS.

O SDK suporta atualmente várias Soluções da Adobe Experience Cloud, incluindo Analytics, Target, Audience Manager e Adobe Experience Platform Identity Service. Os métodos apresentam prefixos de acordo com a solução a qual estão associados. Logo, os métodos do Manager apresentam o prefixo "`audience`audience."

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

   Define a DPID e a DPUUID. Quando definido, os dois serão anexados a cada sinal.

   * A **ID do provedor de dados (DPID)** é a ID do parceiro de dados atribuída pelo Audience Manager.
   * A **ID única de usuário do provedor de dados (DPUUID)** é a ID única do provedor de dados para o usuário.

      >[!IMPORTANT]
      >
      >Antes da versão 4.13. x, DPUUID não era codificado automaticamente. A partir da versão 4.13.x, o SDK primeiro decodifica o valor passado e depois codifica novamente esse valor. Esse processo assegura que o SDK não interfere na compatibilidade com versões anteriores.

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
