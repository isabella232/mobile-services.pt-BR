---
description: 'Os seguintes métodos de aquisição são fornecidos pela biblioteca do iOS '
seo-description: 'Os seguintes métodos de aquisição são fornecidos pela biblioteca do iOS '
seo-title: Métodos de aquisição
solution: Experience Cloud,Analytics
title: Métodos de aquisição
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '93'
ht-degree: 100%

---


# Métodos de aquisição {#acquisition-methods}

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


