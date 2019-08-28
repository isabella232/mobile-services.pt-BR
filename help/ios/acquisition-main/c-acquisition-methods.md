---
description: 'Os seguintes métodos de aquisição são fornecidos pela biblioteca do iOS '
seo-description: 'Os seguintes métodos de aquisição são fornecidos pela biblioteca do iOS '
seo-title: Métodos de aquisição
solution: Marketing Cloud, Analytics
title: Métodos de aquisição
uuid: 6 f 88 de 57-793 d -4 d 33-9 a 54-f 6714289 fd 2 c
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Acquisition methods {#acquisition-methods}

Os seguintes métodos de aquisição são fornecidos pela biblioteca do iOS:

O método a seguir é suportado:

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


