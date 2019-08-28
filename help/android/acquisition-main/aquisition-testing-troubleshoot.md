---
description: As informações a seguir ajudam a solucionar problemas de teste de aquisição.
keywords: android; Aquisição; testando
seo-description: As informações a seguir ajudam a solucionar problemas de teste de aquisição.
seo-title: Solução de problemas de teste de aquisição
solution: Marketing Cloud, Analytics
title: Solução de problemas de teste de aquisição
translation-type: tm+mt
source-git-commit: da8798d7ee1f05dcade31cced5404d78c9cf360a

---


# Solução de problemas de teste de aquisição {#aquistion-testing-troubleshooting}

Estes são alguns problemas que você pode enfrentar ao testar Aquisição e algumas soluções possíveis:

* Caso contrário, o arquivo adbmobileconfig. json deverá ser colocado na pasta assets.

* O nome diferencia maiúsculas de minúsculas. Portanto, não forneça um nome em letras minúsculas.

   É necessário garantir `Config.setContext(this.getApplicationContext())` que é chamado a partir da atividade principal. Para obter mais informações, consulte [Métodos de configuração](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html).

* Há algumas permissões de usuário ausentes no arquivo AndroidManifest.xml fornecido, elas devem enviar dados e gravar chamadas de rastreamento offline:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Na configuração, se o tempo limite do referenciador estiver definido `referrerTimeout: 5`como, isso significa que você precisa enviar o propósito de instalação em um período de 5 segundos depois que o aplicativo foi instalado e iniciado pela primeira vez para ver as informações do referenciador anexadas à ocorrência de instalação.

   Para teste manual, aumente o `referrerTimeout` para 10-15 segundos, de modo que haja tempo suficiente para enviar as informações do referenciador antes que a ocorrência de instalação seja processada.

* É importante executar todas as etapas na [aquisição do Link de publicidade](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) em ordem e garantir que você execute `adb` o shell e o seguinte:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Você deve executar esses dois comandos independentemente para processar o referenciador corretamente. Caso contrário, elimina `adb` duas vezes as informações do referenciador, e os dados recebidos pelo receptor da transmissão ficarão incompletos.
