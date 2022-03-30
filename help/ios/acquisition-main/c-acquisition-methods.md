---
description: 'Os seguintes métodos de aquisição são fornecidos pela biblioteca do iOS '
solution: Experience Cloud Services,Analytics
title: Métodos de aquisição
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
exl-id: dd2721ae-b9a6-48b9-bc92-8e12ee551929
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 100%

---

# Métodos de aquisição  {#acquisition-methods}

Os seguintes métodos de aquisição são fornecidos pela biblioteca do iOS:

O seguinte método é compatível:

* **acquisitionCampaignStartForApp:data:**

   Permite aos desenvolvedores iniciar uma campanha de aquisição de aplicativo como se o usuário tivesse clicado em um link. Isso é útil para criar links de aquisição manuais e gerenciar o redirecionamento da loja de aplicativos por conta própria, como com um `SKStoreView`.

   * Esta é a sintaxe para este método:

      ```objective-c
      + (void)acquisitionCampaignStartForApp:(NSString *) appId data:(NSDictionary *)data; 
      ```

   * Esta é a amostra de código para este método:

      ```objective-c
      [ADBMobile acquisitionCampaignStartForApp:@"0652024f-adcd-49f9-9bd7-2552a4564d2f" data:@{@"custom.key":@"value"}]; 
      ```
