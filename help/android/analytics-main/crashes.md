---
description: Essas informações ajudam a entender como as falhas são rastreadas e as práticas recomendadas para lidar com falsas falhas.
solution: Experience Cloud,Analytics
title: Rastreamento de falhas do aplicativo
topic-fix: Developer and implementation
uuid: 3ab98c14-ccdf-4060-ad88-ec07c1c6bf07
exl-id: d8d59b4e-0231-446d-9ba1-8a9809be9c61
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 100%

---

# Rastreamento de falhas do aplicativo {#track-app-crashes}

Essas informações ajudam a entender como as falhas são rastreadas e as práticas recomendadas para lidar com falsas falhas.

>[!TIP]
>
>As falhas do aplicativo são rastreadas como parte das métricas de ciclo de vida. Antes de rastrear falhas, adicione a biblioteca ao seu projeto e implemente o ciclo de vida. Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto IntelliJ IDEA ou Eclipse* na [Implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).

Quando as medições de ciclo de vida são implementadas, é feita uma chamada `Config.collectLifecycleData` no método `OnResume` para cada atividade. No método `onPause`, é feita uma chamada para `Config.pauseCollectingLifeCycleData`.

Em `pauseCollectingLifeCycleData`, é definido um sinalizador pra indicar uma saída. Quando o aplicativo é inicializado novamente ou retomado, o `collectLifecycleData` seleciona esse sinalizador. Se o aplicativo não for bem sucedido ao sair, como determinado pelo status do sinalizador, um dado de contexto `a.CrashEvent` é enviado com a próxima chamada, e é reportado um evento de falha.

Para assegurar um relatório de falhas preciso, você deve chamar `pauseCollectingLifeCycleData` no método `onPause` de cada atividade. Para entender porque isso é essencial, esta é uma ilustração do ciclo de vida de uma atividade no Android:

![](assets/android-lifecycle.png)

Para obter mais informações sobre o ciclo de vida da atividade do Android, consulte [Atividades](https://developer.android.com/guide/components/activities.html).

*Esta ilustração do ciclo de vida do Android foi criada e [compartilhada pelo Projeto de fonte aberta do Android](https://source.android.com/) e usado de acordo com os termos na [Licença de atribuição dos Comuns criativos 2.5](https://creativecommons.org/licenses/by/2.5/).*

## O que pode causar o relato de falhas falsas?

1. Se estiver fazendo uma depuração com um IDE, como o Android Studio, iniciar o aplicativo novamente a partir do IDE enquanto o aplicativo está em primeiro plano causa uma falha.

   >[!TIP]
   >
   >É possível evitar essa falha colocando o aplicativo em segundo plano antes de iniciar novamente pelo IDE.

1. Se a última atividade em primeiro plano do aplicativo for posta em segundo plano e não fizer chamada `Config.pauseCollectingLifecycleData();` no `onPause`, e se seu aplicativo for fechado manualmente ou suspenso pelo OS, a próxima inicialização resultará em falha.

## Como gerenciar os Fragmentos?

Os fragmentos têm eventos de ciclo de vida do aplicativo semelhantes a Atividades. No entanto, um Fragmento não pode estar ativo sem estar anexado a uma Atividade.

>[!IMPORTANT]
>
>É necessário confiar nos eventos do ciclo de vida contra os quais as atividades relativas podem executar seu código. Isso será tratado pela exibição principal do Fragmento.

## (Opcional) Implementar chamadas de retorno do ciclo de vida da Atividade

A partir da API nível 14, o Android permite chamadas de retorno de ciclos de vida globais nas atividades. Para obter mais informações, consulte [Aplicativo](https://developer.android.com/reference/android/app/Application).

É possível usar essas chamadas de retorno para garantir que todas as atividades façam chamadas `collectLifecycleData()` e `pauseCollectingLifecycleData()` de maneira correta. É necessário adicionar esse código apenas na Atividade principal e qualquer outra Atividade no site que pode ser iniciada pelo aplicativo:

```js
import com.adobe.mobile.Config; 
  
public class MainActivity extends Activity { 
... 
    @Override 
    protected void onCreate(Bundle savedInstanceState) { 
        super.onCreate(savedInstanceState); 
        setContentView(R.layout.activity_main); 
  
        getApplication().registerActivityLifecycleCallbacks(new Application.ActivityLifecycleCallbacks() { 
            @Override 
            public void onActivityResumed(Activity activity) { 
                Config.setContext(activity.getApplicationContext()); 
                Config.collectLifecycleData(activity); 
            } 
  
            @Override 
            public void onActivityPaused(Activity activity) {     
                Config.pauseCollectingLifecycleData(); 
            } 
    
            // the following methods aren't needed for our lifecycle purposes, but are required to be implemented 
            // by the ActivityLifecycleCallbacks object 
            @Override 
            public void onActivityCreated(Activity activity, Bundle savedInstanceState) {} 
            @Override 
            public void onActivityStarted(Activity activity) {} 
            @Override 
            public void onActivityStopped(Activity activity) {} 
            @Override 
            public void onActivitySaveInstanceState(Activity activity, Bundle outState) {} 
            @Override 
            public void onActivityDestroyed(Activity activity) {} 
        }); 
    } 
... 
}
```

Para enviar dados de contexto adicionais na chamada do ciclo de vida usando `Config.collectLifecycleData(Activity activity`, `Map<String`, `Object> contextData)`, é necessário substituir o método `onResume` daquela atividade e realizar uma chamada `super.onResume()` após fazer uma chamada `collectLifecycleData` manualmente.

```js
@Override 
protected void onResume() { 
    HashMap<String, Object> cdata = new HashMap<>(); 
    cdata.put("someKey", "someValue"); 
    Config.collectLifecycleData(this, cdata); 
  
    super.onResume(); 
}
```
