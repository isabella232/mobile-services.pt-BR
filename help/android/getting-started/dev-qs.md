---
description: Estas informações ajudam a implementar a biblioteca do Android e coletar medições de ciclo de vida, como lançamentos, atualizações, sessões, usuários envolvidos e assim por diante.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: Estas informações ajudam a implementar a biblioteca do Android e coletar medições de ciclo de vida, como lançamentos, atualizações, sessões, usuários envolvidos e assim por diante.
seo-title: Implementação principal e ciclo de vida
solution: Marketing Cloud, Analytics
title: Implementação principal e ciclo de vida
topic: Desenvolvedor e implementação
uuid: af 4 d 11 ac -8245-46 a 0-9 b 3 a -4 a 0 a 29 cfbbb 2
translation-type: tm+mt
source-git-commit: c4da3599c858bfbccb7af954df75f94eb7d8e99a

---


# Core implementation and lifecycle {#core-implementation-and-lifecycle}

Estas informações ajudam a implementar a biblioteca do Android e coletar medições de ciclo de vida, como lançamentos, atualizações, sessões, usuários envolvidos e assim por diante.

## Baixar o SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>Para baixar o SDK, é necessário usar o Android 2.2 ou posterior.

1. Conclua as etapas nas seções a seguir para configurar um conjunto de relatórios de desenvolvimento e baixar uma versão já preenchida do arquivo de configuração:

   * [Criar um conjunto de relatórios](/help/android/getting-started/requirements.md)
   * [Baixar o SDK](/help/android/getting-started/requirements.md)

1. Baixe e descompacte o `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip` arquivo e verifique se os seguintes componentes de software existem:

   * `adobeMobileLibrary.jar`, que é a biblioteca que será usada com dispositivos e simuladores Android.

   * `ADBMobileConfig.json`, que é o arquivo de configuração de SDK personalizado para o seu aplicativo.
   >[!IMPORTANT]
   >
   >If you download the SDK outside the Adobe Mobile services UI, the `ADBMobileConfig.json` file must be manually configured. If you are new to Analytics and the Mobile SDK, and you want to set up a development report suite and download a pre-populated version of the configuration file, see [Before You Start](/help/android/getting-started/requirements.md).

## Add the SDK and config file to your IntelliJ IDEA or Eclipse project {#section_B89510FBB4C646AEA73A185B966E54D3}

**Projeto intellij IDEA**

Para adicionar o SDK e o arquivo de configuração ao projeto:

1. Add the `ADBMobileConfig.json` file to the `assets` folder in your project.

1. Clique com o botão direito no seu projeto, no painel Navegação do projeto.
1. Selecione **[!UICONTROL Abrir configurações do módulo]**.
1. Em **[!UICONTROL Configurações do projeto]**, selecione **[!UICONTROL Bibliotecas]**.
1. Click the **[!UICONTROL +]** icon to add a new library.
1. Selecione **[!UICONTROL Java]** e navegue até o arquivo `adobeMobileLibrary.jar`.
1. Selecione os módulos nos quais planeja usar a biblioteca móvel.
1. Clique em **[!UICONTROL Aplicar]** e em **[!UICONTROL OK]para fechar a janela Configurações do módulo.**

**Projeto do Eclipse**

Para adicionar o SDK e o arquivo de configuração ao projeto:

1. Add the `ADBMobileConfig.json` file to the `assets` folder in your project.
1. In **[!UICONTROL Eclipse IDE]**, right-click the project name.
1. Click  **[!UICONTROL Build Path]** &gt; **[!UICONTROL Add External Archives]**.
1. Select `adobeMobileLibrary.jar`.
1. Clique em **[!UICONTROL Abrir]**.
1. Right-click the project again and select **[!UICONTROL Build Path]** &gt; **[!UICONTROL Configure Build Path]**.
1. Na guia **[!UICONTROL Fazer pedido e exportar]**, certifique-se de que o **`adobeMobileLibrary.jar`esteja selecionado.**

## Add app permissions {#section_2EAF73ABF6424647B219A63B33B02CD5}

A biblioteca do AppMeasurement pede as seguintes permissões para enviar dados e gravar chamadas de rastreamento offline:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Para adicionar essas permissões, adicione as seguintes linhas no arquivo `AndroidManifest.xml`, localizado no diretório do projeto do aplicativo:

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## Set the application context {#set-application-context}

O código a seguir deve ser adicionado no `onCreate` método da atividade principal:

```java
   @Override
   public void onCreate(BundlesavedInstanceState){
     super.onCreate(savedInstanceState)
     setContentView(R.layout.main);
     Config.setContext(this.getApplicationContext());
   }
````

## Implement lifecycle metrics {#section_BA686C09021F474AADDE8690BBB910F7}

Após habilitar o ciclo de vida, cada vez que o aplicativo é iniciado uma ocorrência é enviada para medir as inicializações, atualizações, usuários engajados e muitas outras métricas. Para obter mais informações, consulte [Medições de ciclo de vida](/help/android/metrics.md).

**Complete as etapas a seguir em cada atividade do aplicativo:**

1. Importe a biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Na função `onResume`, inicie a coleção de dados do ciclo de vida:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
       // -or- Config.collectLifecycleData(this, contextData); 
   }
   ```

1. Na função `onPause`, pause a coleção de dados do ciclo de vida:

   ```java
   @Override 
   public void onPause() { 
       Config.pauseCollectingLifecycleData(); 
   }
   ```

>[!IMPORTANT]
>
>Você deve adicionar essas chamadas a todas as atividades para garantir relatórios de falhas precisos. Para obter mais informações, consulte [Rastrear falhas](/help/android/analytics-main/crashes.md)do aplicativo.

## Incluir dados adicionais com chamadas de ciclo de vida

Para incluir dados adicionais com chamadas de medições de ciclo de vida, passe um parâmetro adicional para o `collectLifecycleData` que contém os dados de contexto:

```java
@Override 
public void onResume() {
    HashMap<String, Object> contextData = new HashMap<String, Object>(); 
    contextData.put("myapp.category", "Game"); 
    Config.collectLifecycleData(this, contextData); 
}
```

Os valores dos dados de contexto adicionais enviados com o `collectLifecycleData` devem ser mapeados para variáveis personalizadas no Adobe Mobile Services:

![](assets/map-variable-lifecycle.png)

As outras medições de ciclo de vida são coletadas automaticamente. Para obter mais informações, consulte [Medições de ciclo de vida](/help/android/metrics.md).

## O que fazer em seguida {#section_BF709684E1DD40EA9169BC1D0D4B37C2}

Conclua as seguintes tarefas:

* [Rastrear estados do aplicativo](/help/android/analytics-main/states.md)
* [Rastrear ações do aplicativo](/help/android/analytics-main/actions.md)

