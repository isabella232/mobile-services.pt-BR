---
description: Os estados são telas ou exibições diferentes do aplicativo. Sempre que um novo estado for exibido no aplicativo (por exemplo, quando um usuário navega da página inicial para o feed de notícias), uma chamada de rastreamento de estado será enviada. No iOS, um estado normalmente é rastreado pelo método viewDidLoad de cada exibição.
seo-description: Os estados são telas ou exibições diferentes do aplicativo. Sempre que um novo estado for exibido no aplicativo (por exemplo, quando um usuário navega da página inicial para o feed de notícias), uma chamada de rastreamento de estado será enviada. No iOS, um estado normalmente é rastreado pelo método viewDidLoad de cada exibição.
seo-title: Rastrear estados do aplicativo
solution: Marketing Cloud, Analytics
title: Rastrear estados do aplicativo
topic: Desenvolvedor e implementação
uuid: 12 cca 4 eb -1 f 15-4 cec-a 58 f -76 b 69 eaff 99 d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Rastrear estados do aplicativo {#track-app-states}

Os estados são telas ou exibições diferentes do aplicativo. Sempre que um novo estado for exibido no aplicativo (por exemplo, quando um usuário navega da página inicial para o feed de notícias), uma chamada de rastreamento de estado será enviada. No iOS, um estado normalmente é rastreado pelo método viewDidLoad de cada exibição.

>[!TIP]
>
>To track states, make a call to `trackState`. Os estados não são rastreados automaticamente.

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o Arquivo de configuração ao projeto* na [Implementação principal e no ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe a biblioteca.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Chame `trackState` para enviar uma ocorrência para esta exibição de estado.

   ```objective-c
   [ADBMobile trackState:@"Login Screen"  
                    data:nil];
   ```

Nos Adobe Mobile Services, o **[!UICONTROL State Name]** é relatado na variável *`View State`e uma exibição será registrada para cada chamada*. `trackState` Em outras interfaces do Analytics, o **[!UICONTROL Exibir estado]** é reportado como **[!UICONTROL Nome de página]** e as exibições de estado como exibições de páginas.

## Sending additional data {#section_CFDB4F944496401786A145C209AB387C}

In addition to the **[!UICONTROL State Name]**, you can send additional context data with each track action call:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"logged in" forKey:@"myapp.login.LoginStatus"]; 
[ADBMobile trackState:@"Home Screen" data:contextData];
```

Os valores de dados de contexto devem ser mapeados para variáveis personalizadas:

![](assets/map-variable-context-state.png)

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Os estados geralmente são vistos usando um relatório de definição de caminho para que você possa ver como os usuários navegam no seu aplicativo e quais estados são exibidos mais.

|  |  |
|--- |--- |
| Adobe Mobile Services | O relatório **[!UICONTROL Exibir estados.]** Este relatório está baseado nos caminhos que o usuário tomou pelo aplicativo. A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics | Os estados podem ser exibidos em qualquer lugar em que as Páginas podem ser exibidas, como o relatório **Páginas**, o relatório **[!UICONTROL Exibições da página]** e relatórios de **Caminho[!UICONTROL .]** |
| Ad hoc analytics | Os estados podem ser exibidos em qualquer lugar em que as Páginas possam ser exibidas usando a dimensão **Página**, a métrica **[!UICONTROL Exibições da página]** e os relatórios de **Caminho[!UICONTROL .]** |
