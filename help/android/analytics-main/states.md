---
description: Os estados são telas ou exibições diferentes no aplicativo.
seo-description: Os estados são telas ou exibições diferentes no aplicativo.
seo-title: Rastrear estados do aplicativo
solution: Marketing Cloud,Analytics
title: Rastrear estados do aplicativo
topic: Desenvolvedor e implementação
uuid: 69c99d05-5816-4c86-97c5-d218dc26c129
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Rastrear estados do aplicativo {#track-app-states}

Os estados são telas ou exibições diferentes no aplicativo.

Sempre que um novo estado for exibido no aplicativo, por exemplo, quando um usuário navega de uma página inicial para a tela de feed de notícias, uma chamada de `trackState` é enviada. No Android, o `trackState` normalmente é chamado sempre que uma nova atividade é carregada.

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto* IntelliJ IDEA ou Eclipse na implementação e ciclo de vida [principal](/help/android/getting-started/dev-qs.md).

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

The `"State Name"` is reported in the `View State` variable in Adobe Mobile services, and a view is recorded for each `trackState` call. Em outras interfaces do Analytics, `View State` é reportado como `Page Name`e `state views` como `page views`.

## Send additional data {#section_CFDB4F944496401786A145C209AB387C}

In addition to the `"State Name"`, you can send additional context data with each track action call:

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

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Os estados normalmente são visualizados usando um relatório de definição de caminho, que permite visualizar como os usuários navegam no aplicativo e quais estados são visualizados com frequência.

|  |  |
|--- |--- |
| Adobe Mobile Services | O relatório **[!UICONTROL Exibir estados.]** Este relatório está baseado nos caminhos que o usuário tomou pelo aplicativo. A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics | Os estados podem ser exibidos em qualquer lugar em que as Páginas podem ser exibidas, como o relatório **Páginas**, o relatório **[!UICONTROL Exibições da página]** e relatórios de **Caminho[!UICONTROL .]** |
| Ad hoc analytics | Os estados podem ser exibidos em qualquer lugar em que as Páginas possam ser exibidas usando a dimensão **Página**, a métrica **[!UICONTROL Exibições da página]** e os relatórios de **Caminho[!UICONTROL .]** |


