---
description: Os estados são telas ou exibições diferentes no aplicativo.
seo-description: Os estados são telas ou exibições diferentes no aplicativo.
seo-title: Rastrear estados do aplicativo
solution: Experience Cloud,Analytics
title: Rastrear estados do aplicativo
topic: Developer and implementation
uuid: 69c99d05-5816-4c86-97c5-d218dc26c129
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 100%

---


# Rastrear estados do aplicativo {#track-app-states}

Os estados são telas ou exibições diferentes no aplicativo.

Sempre que um novo estado for exibido no aplicativo, por exemplo, quando um usuário navega de uma página inicial para a tela de feed de notícias, uma chamada de `trackState` é enviada. No Android, o `trackState` normalmente é chamado sempre que uma nova atividade é carregada.

## Rastreamento de estados {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto IntelliJ IDEA ou Eclipse* na [Implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Importe a biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Na função `onCreate`, faça uma chamada com `trackState` para enviar uma ocorrência dessa exibição de estado:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Adobe - track when this state loads 
       Analytics.trackState("State Name", null); 
   }
   ```

O `"State Name"` é relatado na variável `View State` no Adobe Mobile Services, e uma exibição é gravada para cada chamada `trackState`. Em outras interfaces do Analytics, `View State` é reportado como `Page Name`, e `state views` é reportado como `page views`.

## Enviar dados adicionais {#section_CFDB4F944496401786A145C209AB387C}

Além do `"State Name"`, é possível enviar dados de contexto adicionais com cada chamada de rastreamento de ação:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
    super.onCreate(savedInstanceState); 
    setContentView(R.layout.main); 
  
    // Adobe - track when this state loads 
    HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
    exampleContextData.put("myapp.login.LoginStatus", "logged in"); 
    Analytics.trackState("Home Screen", exampleContextData); 
}
```

Os valores de dados de contexto devem ser mapeados para variáveis personalizadas nos Adobe Mobile Services:

![](assets/map-variable-context-state.png)

## Relatório do estado do aplicativo {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Os estados geralmente são vistos usando um relatório de definição de caminho para que você possa ver como os usuários navegam no seu aplicativo e quais estados são exibidos com mais frequência.

|  |  |
|--- |--- |
| Adobe Mobile Services | O relatório **[!UICONTROL Exibir estados]**. Este relatório está baseado nos caminhos que o usuário tomou pelo aplicativo. Um caminho de amostra é  **[!UICONTROL Início]** > **[!UICONTROL Configurações]** > **[!UICONTROL Feed]**. |
| Adobe Analytics | Os estados podem ser exibidos em qualquer lugar em que as Páginas podem ser exibidas, como o relatório **[!UICONTROL Páginas]**, o relatório **[!UICONTROL Exibições da página]** e relatórios de **[!UICONTROL Caminho]**. |
| Ad hoc analytics | Os estados podem ser exibidos em qualquer lugar em que as Páginas possam ser exibidas usando a dimensão **[!UICONTROL Página]**, a métrica **[!UICONTROL Exibições da página]** e os relatórios de **[!UICONTROL Caminho]**. |


