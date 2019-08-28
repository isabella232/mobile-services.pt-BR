---
description: Este tópico fornece informações sobre como solucionar problemas que você pode enfrentar durante testes de aquisição.
keywords: android; biblioteca; dispositivos móveis; sdk
seo-description: Este tópico fornece informações sobre como solucionar problemas que você pode enfrentar durante testes de aquisição.
seo-title: Solução de problemas de teste de aquisição
solution: Marketing Cloud, Analytics
title: Solução de problemas de teste de aquisição
topic: Desenvolvedor e implementação
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# Solução de problemas de teste de aquisição {#troubleshoot-acquisition-testing}

Este tópico fornece informações sobre como solucionar problemas que você pode enfrentar durante testes de aquisição.

* Caso contrário, o arquivo adbmobileconfig. json deverá ser colocado na `assets` pasta.

   O nome diferencia maiúsculas de minúsculas, portanto, não use letras maiúsculas e minúsculas.

* Verifique se `Config.setContext(this.getApplicationContext())` é chamado da atividade principal.

   Para obter mais informações, consulte [Métodos de configuração](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html).

* Verifique se as permissões necessárias para o SDK móvel estão presentes no `AndroidManifest.xml` arquivo:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Se for `referrerTimeout` definido como 5 no arquivo admobileconfig. json, é necessário enviar o propósito de instalação em um período de 5 segundos depois que o aplicativo foi instalado e iniciado pela primeira vez para ver as informações do referenciador anexadas à ocorrência de instalação.

   Para o teste manual, recomendamos que você aumente o `referrerTimeout` para 10-15 segundos, para que você tenha tempo suficiente para enviar as informações do referenciador antes que a ocorrência de instalação seja processada.

* Execute todas as etapas na [aquisição do Link de publicidade](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) e certifique-se de executar o `adb shell` comando primeiro e depois o seguinte:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Para processar o referenciador corretamente, você deve executar esses dois comandos independentemente. Caso contrário `adb` , serão ignoradas duas vezes as informações do referenciador e os dados recebidos pelo receptor da transmissão ficarão incompletos.

