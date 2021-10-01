---
description: Este tópico oferece informações sobre como solucionar problemas possíveis durante o teste de aquisição.
keywords: android;biblioteca;móvel;sdk
solution: Experience Cloud,Analytics
title: Resolução de problemas de teste de aquisição
topic-fix: Developer and implementation
exl-id: 1ed2ad89-4e89-43da-aa21-f688b4d1c0d1
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 100%

---

# Resolução de problemas de teste de aquisição {#troubleshoot-acquisition-testing}

Este tópico oferece informações sobre como solucionar problemas possíveis durante o teste de aquisição.

* Caso não seja especificado, o arquivo ADBMobileConfig.json deve ser colocado na pasta `assets`.

   O nome diferencia maiúsculas de minúsculas, portanto, não use letras maiúsculas ou minúsculas.

* Verifique se `Config.setContext(this.getApplicationContext())` é chamado da atividade principal.

   Para obter mais informações, consulte [Métodos de configuração](../configuration/methods.md).

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

* Execute todas as etapas em [Teste de aquisições via links de publicidade](t-testing-marketing-link-acquisition.md), certifique-se de executar o comando `adb shell` primeiro e, em seguida, execute o seguinte:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Para o correto processamento da intenção do referenciador, você deve executar esses dois comandos separadamente. Caso contrário, `adb` omitirá as informações do referenciador duas vezes e os dados recebidos pelo receptor da transmissão estarão incompletos.
