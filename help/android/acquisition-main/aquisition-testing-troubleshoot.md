---
description: As seguintes informações ajudam a solucionar problemas de teste de aquisição.
keywords: android;Aquisição;teste;android;Acquisition;testing
seo-description: As seguintes informações ajudam a solucionar problemas de teste de aquisição.
seo-title: Solução de problemas de teste de aquisição
solution: Marketing Cloud,Analytics
title: Solução de problemas de teste de aquisição
translation-type: tm+mt
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# Solução de problemas de teste de aquisição {#aquistion-testing-troubleshooting}

Estes são alguns problemas que você pode enfrentar ao testar a Aquisição e algumas soluções possíveis:

* Caso contrário, o arquivo ADBMobileConfig.json deve ser colocado na pasta assets.

* O nome diferencia maiúsculas de minúsculas, portanto, não forneça um nome em letras minúsculas.

   É necessário garantir que a atividade principal `Config.setContext(this.getApplicationContext())` seja chamada. Para obter mais informações, consulte Métodos [](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)de configuração.

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
