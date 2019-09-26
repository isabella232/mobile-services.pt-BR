---
description: The following information helps you troubleshoot Acquisition testing issues.
keywords: android;Acquisition;testing
seo-description: The following information helps you troubleshoot Acquisition testing issues.
seo-title: Troubleshooting Acquisition testing
solution: Marketing Cloud,Analytics
title: Troubleshooting Acquisition testing
translation-type: tm+mt
source-git-commit: da8798d7ee1f05dcade31cced5404d78c9cf360a

---


# Troubleshooting Acquisition testing {#aquistion-testing-troubleshooting}

Here are some issues you might face when testing Acquisition and some possible solutions:

* If not otherwise specified, the ADBMobileConfig.json file should be placed in the assets folder.

* The name is case sensitive, so do not provide a name in lower-case letters.

   You need to ensure that  is called from the main activity. `Config.setContext(this.getApplicationContext())` For more information, see Configuration methods.[](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)

* Há algumas permissões de usuário ausentes do arquivo AndroidManifest.xml fornecido, necessárias para enviar dados e gravar chamadas de rastreamento offline:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Na sua configuração, se o tempo limite do referenciador estiver definido como `referrerTimeout: 5`, isso significa que você precisa enviar o propósito de instalação em um período de 5 segundos após a instalação e inicialização do aplicativo pela primeira vez para ver as informações do referenciador anexadas à ocorrência de instalação.

   Para testes manuais, aumente `referrerTimeout` para 10 a 15 segundos, para que haja tempo suficiente para enviar as informações do referenciador antes que a ocorrência de instalação seja processada.

* É importante executar todas as etapas em [Testar a aquisição](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) do Marketing Link para garantir que você execute o shell e, em seguida, execute o `adb` seguinte:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Você deve executar esses dois comandos independentemente para processar o propósito do referenciador corretamente.  Caso contrário, `adb` evita-se duas vezes as informações do referenciador e os dados recebidos pelo receptor da transmissão estarão incompletos.
