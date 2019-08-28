---
description: As ações são eventos que ocorrem no aplicativo que você deseja avaliar. Cada ação tem uma ou mais métricas correspondentes, que são aumentadas sempre que o evento ocorre. Por exemplo, é possível rastrear uma nova assinatura sempre que um artigo for visualizado ou um nível for concluído. As métricas correspondentes a esses eventos são configuradas como assinaturas, artigos lidos e níveis concluídos.
seo-description: As ações são eventos que ocorrem no aplicativo que você deseja avaliar. Cada ação tem uma ou mais métricas correspondentes, que são aumentadas sempre que o evento ocorre. Por exemplo, é possível rastrear uma nova assinatura sempre que um artigo for visualizado ou um nível for concluído. As métricas correspondentes a esses eventos são configuradas como assinaturas, artigos lidos e níveis concluídos.
seo-title: Rastrear ações do aplicativo
solution: Marketing Cloud, Analytics
title: Rastrear ações do aplicativo
topic: Desenvolvedor e implementação
uuid: 62017 be 1-5395-4 d 16-bde 3-4 c 40 a 2 c 012 d 4
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Rastrear ações do aplicativo {#track-app-actions}

As ações são eventos que ocorrem no aplicativo que você deseja avaliar. Cada ação tem uma ou mais métricas correspondentes, que são aumentadas sempre que o evento ocorre. Por exemplo, é possível rastrear uma nova assinatura sempre que um artigo for visualizado ou um nível for concluído. As métricas correspondentes a esses eventos são configuradas como assinaturas, artigos lidos e níveis concluídos.

As ações não são rastreadas automaticamente. Portanto para rastrear um evento é necessário chamar `trackAction`.

## Tracking actions {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o Arquivo de configuração ao projeto* na [Implementação principal e no ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe a biblioteca.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Quando a ação que deseja rastrear ocorrer em seu aplicativo, chame `trackAction` para enviar uma ocorrência para esta ação.

   ```objective-c
   [ADBMobile trackAction:@"myapp.ActionName"  
                     data:nil];
   ```

   >[!TIP]
   >
   >If the code where you are adding this call might run while the app is in the background, call `trackActionFromBackground` instead of `trackAction`.

1. In the Adobe Mobile services UI, select your app and click **[!UICONTROL Manage App Settings]**.

1. Clique em **[!UICONTROL Gerenciar variáveis e métricas]** e clique na guia **Métricas personalizadas[!UICONTROL .]**

1. Mapeie o nome do contexto de dados definido em seu código, por exemplo, `a.action=myapp.ActionName`, para um evento personalizado.

   ![](assets/map-event-context-data.png)

Você também pode configurar uma prop para manter todos os valores de ação, mapeando uma prop personalizada com um nome como **[!UICONTROL Ações personalizadas]** e definindo o valor para `a.action`.

![](assets/map-custom-prop.png)

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Além do nome da ação, você pode enviar dados de contexto adicionais com cada chamada de ação de rastreamento:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"Twitter" forKey:@"myapp.social.SocialSource"]; 
[ADBMobile trackAction:@"myapp.SocialShare" data:contextData];
```

Os valores de dados de contexto devem ser mapeados para variáveis personalizadas:

![](assets/map-variable-context-action.png)

## Tracking background actions {#section_AC13013F207D4FBAAF27E4412034251E}

Se você estiver rastreando uma ação no código que pode ser executada quando o aplicativo estiver em segundo plano, chame `trackActionFromBackground` em vez de `trackAction`. Embora `trackActionFromBackground` contenha alguma lógica adicional para evitar que as chamadas de ciclo de vida disparem quando não deveriam, os parâmetros são os mesmos.

## Action reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| Interface | Relatório |
|--- |--- |
| Adobe Mobile Services | **** Relatório dos Caminhos de ação. Veja a ordem em que as ações ocorrem em seu aplicativo. Você também pode clicar em **[!UICONTROL Personalizar]em qualquer relatório para ver as ações classificadas, apresentadas em ordem de tendência ou em um relatório detalhado, ou aplicar um filtro para ver as ações de um segmento específico.** |
| Relatórios e análises de marketing | **[!UICONTROL Relatório de Evento personalizado.]**  Depois que uma ação é mapeada a um evento personalizado, é possível visualizar os eventos móveis semelhantes a todos os outros eventos do Analytics. |
| Ad hoc analytics | **[!UICONTROL Relatório de Evento personalizado.]** Depois que uma ação é mapeada a um evento personalizado, é possível visualizar os eventos móveis semelhantes a todos os outros eventos do Analytics. |