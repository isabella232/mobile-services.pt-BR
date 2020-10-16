---
description: Estas informações ajudam a implementar a biblioteca do Android e coletar medições de ciclo de vida, como lançamentos, atualizações, sessões, usuários envolvidos e assim por diante.
keywords: android;library;mobile;sdk
seo-description: Estas informações ajudam a implementar a biblioteca do Android e coletar medições de ciclo de vida, como lançamentos, atualizações, sessões, usuários envolvidos e assim por diante.
seo-title: Implementação principal e ciclo de vida
solution: Experience Cloud,Analytics
title: Implementação principal e ciclo de vida
topic: Developer and implementation
uuid: af4d11ac-8245-46a0-9b3a-4a0a29cfbbb2
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '560'
ht-degree: 100%

---


# Implementação principal e ciclo de vida {#core-implementation-and-lifecycle}

Estas informações ajudam a implementar a biblioteca do Android e coletar medições de ciclo de vida, como lançamentos, atualizações, sessões, usuários envolvidos e assim por diante.

## Baixar o SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>Para baixar o SDK, é necessário usar o Android 2.2, ou versão posterior.

1. Complete as etapas nas seções a seguir para configurar um conjunto de relatórios de desenvolvimento e baixar uma versão pré-preenchida do arquivo de configuração:

   * [Criar um conjunto de relatórios](/help/android/getting-started/requirements.md)
   * [Baixar o SDK](/help/android/getting-started/requirements.md)

1. Baixe e descompacte o arquivo `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip` e verifique se os seguintes componentes de software existem:

   * `adobeMobileLibrary.jar`, que é a biblioteca que será usada pelos dispositivos e simuladores Android.

   * `ADBMobileConfig.json`, que é o arquivo de configuração de SDK personalizado para o seu aplicativo.
   >[!IMPORTANT]
   >
   >Se você baixar o SDK fora da interface do Adobe Mobile Services, o arquivo `ADBMobileConfig.json` deverá ser configurado manualmente. Se você nunca usou o Analytics e o Mobile SDK, e deseja configurar um conjunto de relatórios de desenvolvimento e baixar uma versão já preenchida do arquivo de configuração, consulte [Antes de começar](/help/android/getting-started/requirements.md).

## Adicionar o SDK e o arquivo de configuração ao projeto IntelliJ IDEA ou Eclipse {#section_B89510FBB4C646AEA73A185B966E54D3}

**Projeto IntelliJ IDEA**

Para adicionar o SDK e o arquivo de configuração ao projeto:

1. Adicione o arquivo `ADBMobileConfig.json` à pasta `assets` do projeto.

1. Clique com o botão direito no seu projeto, no painel Navegação do projeto.
1. Selecione **[!UICONTROL Abrir configurações do módulo]**.
1. Em **[!UICONTROL Configurações do projeto]**, selecione **[!UICONTROL Bibliotecas]**.
1. Clique no ícone **[!UICONTROL +]** para adicionar uma nova biblioteca.
1. Selecione **[!UICONTROL Java]** e navegue até o arquivo `adobeMobileLibrary.jar`.
1. Selecione os módulos nos quais planeja usar a biblioteca móvel.
1. Clique em **[!UICONTROL Aplicar]** e em **[!UICONTROL OK]** para fechar a janela Configurações do módulo.

**Projeto Eclipse**

Para adicionar o SDK e o arquivo de configuração ao projeto:

1. Adicione o arquivo `ADBMobileConfig.json` à pasta `assets` do projeto.
1. No **[!UICONTROL Eclipse IDE]**, clique com o botão direito do mouse no nome do projeto.
1. Clique em **[!UICONTROL Criar caminho]** > **[!UICONTROL Adicionar arquivos externos]**.
1. Selecione `adobeMobileLibrary.jar`.
1. Clique em **[!UICONTROL Abrir]**.
1. Clique com o botão direito no projeto novamente e selecione **[!UICONTROL Criar caminho]** > **[!UICONTROL Configurar caminho de construção]**.
1. Na guia **[!UICONTROL Fazer pedido e exportar]**, certifique-se de que o **`adobeMobileLibrary.jar`** esteja selecionado.

## Adicionar permissões do aplicativo {#section_2EAF73ABF6424647B219A63B33B02CD5}

A biblioteca do AppMeasurement pede as seguintes permissões para enviar dados e gravar chamadas de rastreamento offline:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Para adicionar essas permissões, adicione as seguintes linhas no arquivo `AndroidManifest.xml`, localizado no diretório do projeto do aplicativo:

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## Definir o contexto do aplicativo {#set-application-context}

O código a seguir deve ser adicionado ao método `onCreate` da atividade principal:

```java
   @Override
   public void onCreate(BundlesavedInstanceState){
     super.onCreate(savedInstanceState)
     setContentView(R.layout.main);
     Config.setContext(this.getApplicationContext());
   }
```

## Implementar métricas de ciclo de vida {#section_BA686C09021F474AADDE8690BBB910F7}

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
>É necessário adicionar essas chamadas em todas as atividades para garantir relatórios de falhas precisos. Para obter mais informações, consulte [Rastrear falhas do aplicativo](/help/android/analytics-main/crashes.md).

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

