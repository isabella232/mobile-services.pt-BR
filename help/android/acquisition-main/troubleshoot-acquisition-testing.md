---
description: Este tópico oferece informações sobre como solucionar problemas possíveis durante o teste de aquisição.
keywords: android;library;mobile;sdk
seo-description: Este tópico oferece informações sobre como solucionar problemas possíveis durante o teste de aquisição.
seo-title: Resolução de problemas de teste de aquisição
solution: Experience Cloud,Analytics
title: Resolução de problemas de teste de aquisição
topic: Developer and implementation
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '248'
ht-degree: 100%

---


# Resolução de problemas de teste de aquisição {#troubleshoot-acquisition-testing}

Este tópico oferece informações sobre como solucionar problemas possíveis durante o teste de aquisição.

* Caso não seja especificado, o arquivo ADBMobileConfig.json deve ser colocado na pasta `assets`.

   O nome diferencia maiúsculas de minúsculas, portanto, não use letras maiúsculas ou minúsculas.

* Verifique se `Config.setContext(this.getApplicationContext())` é chamado da atividade principal.

   Para obter mais informações, consulte [Métodos de configuração](https://docs.adobe.com/content/help/pt-BR/mobile-services/android/configuration-android/methods.html).

* Verifique se as permissões necessárias para o SDK móvel estão presentes no arquivo `AndroidManifest.xml`:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Se o `referrerTimeout` estiver definido como 5 no arquivo ADMobileConfig.json, você deve enviar a intenção de instalação em um período de 5 segundos após a instalação e a inicialização do aplicativo pela primeira vez para ver as informações do referenciador anexadas à ocorrência de instalação.

   Para testes manuais, recomendamos que você aumente o `referrerTimeout` para 10–15 segundos, para que tenha tempo suficiente para enviar as informações do referenciador antes que a ocorrência de instalação seja processada.

* Execute todas as etapas em [Teste de aquisições via links de publicidade](https://docs.adobe.com/content/help/pt-BR/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html), certifique-se de executar o comando `adb shell` primeiro e, em seguida, execute o seguinte:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Para o correto processamento da intenção do referenciador, você deve executar esses dois comandos separadamente. Caso contrário, `adb` omitirá as informações do referenciador duas vezes e os dados recebidos pelo receptor da transmissão estarão incompletos.

