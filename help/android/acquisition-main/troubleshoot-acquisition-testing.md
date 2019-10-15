---
description: Este tópico fornece informações sobre como solucionar problemas que você pode enfrentar durante o teste de aquisição.
keywords: android;biblioteca;móvel;sdk
seo-description: Este tópico fornece informações sobre como solucionar problemas que você pode enfrentar durante o teste de aquisição.
seo-title: Solução de problemas de teste de aquisição
solution: Marketing Cloud,Analytics
title: Solução de problemas de teste de aquisição
topic: Desenvolvedor e implementação
translation-type: tm+mt
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# Solução de problemas de teste de aquisição {#troubleshoot-acquisition-testing}

Este tópico fornece informações sobre como solucionar problemas que você pode enfrentar durante o teste de aquisição.

* Caso contrário, o arquivo ADBMobileConfig.json deve ser colocado na `assets` pasta.

   O nome diferencia maiúsculas de minúsculas, portanto, não use letras maiúsculas ou minúsculas.

* Certifique-se de que `Config.setContext(this.getApplicationContext())` seja chamado da atividade principal.

   Para obter mais informações, consulte Métodos [](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)de configuração.

* Verifique se as permissões necessárias para o SDK móvel estão presentes no `AndroidManifest.xml` arquivo:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Se o `referrerTimeout` estiver definido como 5 no arquivo ADMobileConfig.json, será necessário enviar o propósito de instalação em um período de 5 segundos após a instalação e inicialização do aplicativo pela primeira vez para ver as informações do referenciador anexadas à ocorrência de instalação.

   Para testes manuais, recomendamos que você aumente `referrerTimeout` para 10 a 15 segundos, para que tenha tempo suficiente para enviar as informações do referenciador antes que a ocorrência de instalação seja processada.

* Execute todas as etapas em [Teste da aquisição](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) do Marketing Link e certifique-se de executar o `adb shell` comando primeiro e, em seguida, execute o seguinte:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Para processar a intenção do referenciador corretamente, você deve executar esses dois comandos independentemente. Caso contrário, `adb` as informações do referenciador serão omitidas duas vezes e os dados recebidos pelo receptor da transmissão estarão incompletos.

