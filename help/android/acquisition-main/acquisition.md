---
description: É possível gerar links de aquisição com códigos de rastreamento exclusivos no Adobe Mobile Services. Quando um usuário baixa e executa um aplicativo da loja de aplicativos depois de clicar em um link gerado, o SDK coleta e envia automaticamente os dados de aquisição para o Adobe Mobile Services.
keywords: android;library;mobile;sdk
seo-description: É possível gerar links de aquisição com códigos de rastreamento exclusivos no Adobe Mobile Services. Quando um usuário baixa e executa um aplicativo da loja de aplicativos depois de clicar em um link gerado, o SDK coleta e envia automaticamente os dados de aquisição para o Adobe Mobile Services.
seo-title: Aquisição de aplicativos móveis
solution: Experience Cloud,Analytics
title: Aquisição de aplicativos móveis
topic: Developer and implementation
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '876'
ht-degree: 100%

---


# Aquisição de aplicativos móveis {#mobile-app-acquisition}

É possível gerar links de aquisição com códigos de rastreamento exclusivos no Adobe Mobile Services. Quando um usuário baixa e executa um aplicativo da loja de aplicativos depois de clicar em um link gerado, o SDK coleta e envia automaticamente os dados de aquisição para o Adobe Mobile Services.

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para obter a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>Para usar a Aquisição, você **deve** ter a versão 4.1 ou posterior do SDK.

Os links de aquisição devem ser criados nos Adobe Mobile Services. Para obter mais informações, consulte [Aquisição](/help/using/acquisition-main/acquisition-main.md).

**Nas versões 4.18.0 e posteriores do SDK**:

A partir de 1º de março de 2020, o Google descontinuará o mecanismo de difusão de intenção INSTALL_REFERRER. Para obter mais informações, consulte [Ainda usando o InstallBroadcast? Alterne para a API do referenciador Play até 1º de março de 2020](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html). Para continuar coletando informações do referenciador de instalação da Google Play Store, atualize seu aplicativo para usar a versão 4.18.0 ou mais recente do SDK.

Por causa dessa descontinuação, em vez de criar um `BroadcastReceiver`, é necessário coletar o URL do referenciador de instalação em uma nova API do Google e passar o URL resultante para o SDK.

1. Adicione o pacote Referenciador de instalação do Google Play às dependências do arquivo do Gradle:

   `implementation 'com.android.installreferrer:installreferrer:1.1'`

1. Para recuperar o URL da API do Referenciador de instalação, conclua as etapas em [Obter o Referenciador de instalação](https://developer.android.com/google/play/installreferrer/library#install-referrer).

1. Passe o URL do referenciador para o SDK:

   `Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);`

>[!IMPORTANT]
>
>Para evitar chamadas desnecessárias de API em seu aplicativo, o Google recomenda que você chame a API apenas uma vez, imediatamente após a instalação.

Para decidir a melhor maneira de usar as APIs do Referenciador de instalação do Google Play no aplicativo, consulte a documentação do Google. Esse é um exemplo de como usar o Adobe SDK com as APIs de referência de instalação do Google Play:

```java
void handleGooglePlayReferrer() {
    // Google recommends only calling this API the first time you need it:
    // https://developer.android.com/google/play/installreferrer/library#install-referrer

    // Store a boolean in SharedPreferences to ensure we only call it once.
    final SharedPreferences prefs = getSharedPreferences("acquisition", 0);
    if (prefs != null) {
        if (prefs.getBoolean("referrerHasBeenProcessed", false)) {
            return;
        }
    }

    final InstallReferrerClient referrerClient = InstallReferrerClient.newBuilder(getApplicationContext()).build();
    referrerClient.startConnection(new InstallReferrerStateListener() {
        private boolean complete = false;

        @Override
        public void onInstallReferrerSetupFinished(int responseCode) {
            switch (responseCode) {
                case InstallReferrerClient.InstallReferrerResponse.OK:
                    // connection is established
                    complete();
                    try {
                        final ReferrerDetails details = referrerClient.getInstallReferrer();                        

                        // pass the install referrer url to the SDK
                        Analytics.processGooglePlayInstallReferrerUrl(details.getInstallReferrer());

                    } catch (final RemoteException ex) {
                        Log.w("Acquisition - RemoteException while retrieving referrer information (%s)", ex.getLocalizedMessage() == null ? "unknown" : ex.getLocalizedMessage());
                    } finally {
                        referrerClient.endConnection();
                    }
                    break;
                case InstallReferrerClient.InstallReferrerResponse.FEATURE_NOT_SUPPORTED:
                case InstallReferrerClient.InstallReferrerResponse.SERVICE_UNAVAILABLE:
                default:
                    // API not available in the Play Store app - nothing to do here
                    complete();
                    referrerClient.endConnection();
                    break;
            }
        }

        @Override
        public void onInstallReferrerServiceDisconnected() {
            if (!complete) {
                // something went wrong trying to get a connection, try again
                referrerClient.startConnection(this);
            }
        }

        void complete() {
            complete = true;
            SharedPreferences.Editor editor = getSharedPreferences("acquisition", 0).edit();
            editor.putBoolean("referrerHasBeenProcessed", true);
            editor.apply();
        }
    });
}
```

**Nas versões 4.13.1 e posteriores do SDK**:

Se você não puder usar os links de aquisição criados no Adobe Mobile Services, os dados de aquisição ainda poderão ser coletados e enviados pelo SDK com o Google Play Acquisition.

Para coletar os dados de aquisição de uma campanha padrão do Google Play Acquisition:

* Use o método de aquisição padrão da Google Play Store.

   Os dados de aquisição personalizados podem ser usados com os pares de valores principais padrão do Google Play Acquisition.

* Quando um usuário baixa e executa um aplicativo como o resultado de uma aquisição da Google Play Store, os dados do referenciador são coletados e enviados para o Adobe Mobile Services.

   * Os dados são armazenados e disponibilizados na instância `AdobeDataCallback` registrada anteriormente com o SDK.

      Para obter mais informações, consulte [Métodos de configuração](/help/android/configuration/methods.md).

   * Os tipos de evento `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` ou `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` são usados.

   * As chaves personalizadas que faziam parte dos dados de aquisição do Google Play terão &quot;`a.acquisition.custom.`&quot; no nome.

Se você estiver usando os links do Acquisition criados no Adobe Mobile Services, adicione dados personalizados ao link de aquisição quando concluir as seguintes tarefas:

1. Coloque o prefixo &quot;`adb`&quot; em uma variável da aquisição.

   Quando o SDK recebe os dados de aquisição do Adobe Mobile Services na primeira inicialização, os dados são armazenados e ficam disponíveis na instância `AdobeDataCallback` que foi registrada anteriormente com o SDK. Para obter mais informações, consulte [Métodos de configuração](/help/android/configuration/methods.md).

1. O tipo de evento `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` ou `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` será usado.

1. As chaves de dados personalizadas recebem o prefixo “`a.acquisition.custom.`”

>[!TIP]
>
>Se estiver enviando dados para diversos conjuntos de relatórios, use os dados de aquisição do aplicativo que está associado ao primeiro conjunto de relatórios na lista de IDs de conjuntos de relatórios.

As atualizações nessa seção permitem que o SDK envie dados de aquisição a partir de um link de aquisição.

## Rastreamento de aquisição móvel {#section_CEA30C652AC8470784B8054E299B80FA}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto IntelliJ IDEA ou Eclipse* na [Implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Importe a biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Implemente `BroadcastReceiver` para o referenciador:

   ```java
   package com.your.package.name;  // replace with your app package name
   
   import android.content.BroadcastReceiver;
   import android.content.Context;
   import android.content.Intent;
   
   public class GPBroadcastReceiver extends BroadcastReceiver {
     @Override
     public void onReceive(Context c, Intent i) {
      com.adobe.mobile.Analytics.processReferrer(c, i);
     }
   }
   ```

1. Atualize `AndroidManifest.xml` para habilitar `BroadcastReceiver` criado na etapa anterior:

   ```xml
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
     <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
   </receiver>
   ```

1. Verifique se o arquivo `ADBMobileConfig.json` contém as configurações de aquisição exigidas:

   ```xml
   "acquisition": {
      "server": "c00.adobe.com",
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f"
   },
   "analytics": {
     "referrerTimeout": 5,
     ...
   ```

   >[!IMPORTANT]
   >
   >Se estiver enviando dados para vários conjuntos de relatórios, use as configurações de aquisição (servidor de aquisição e appid) do aplicativo associado ao primeiro conjunto de relatórios na sua lista de IDs de conjuntos de relatórios.

   As configurações `acquisition` são geradas pelo Adobe Mobile Services e não devem ser alteradas. Para obter mais informações sobre como baixar um arquivo `ADBMobileConfig.json` personalizado com as configurações de `acquisition` predefinidas, consulte [Antes de iniciar](/help/android/getting-started/requirements.md).

Quando estas configurações estiverem habilitadas, após a primeira inicialização do aplicativo, os dados de aquisição serão enviados automaticamente com a chamada de ciclo de vida inicial.

>[!CAUTION]
>
>`referrerTimeout` deve ser definido com um valor maior que 0 para habilitar a aquisição do aplicativo.
