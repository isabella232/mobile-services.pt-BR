---
description: As informações seguintes ajudam a solucionar problemas de teste de aquisição.
keywords: android;Acquisition;testing
seo-description: As informações seguintes ajudam a solucionar problemas de teste de aquisição.
seo-title: Resolução de problemas de teste de aquisição
solution: Experience Cloud,Analytics
title: Resolução de problemas de teste de aquisição
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 100%

---


# Resolução de problemas de teste de aquisição {#aquistion-testing-troubleshooting}

Veja a seguir alguns problemas que você pode enfrentar ao testar a aquisição e algumas soluções possíveis:

* Não sendo especificado de outra maneira, o arquivo ADBMobileConfig.json deve ser colocado na pasta de ativos.

* O nome diferencia maiúsculas de minúsculas, portanto, não forneça um nome em letras minúsculas.

   É necessário garantir que `Config.setContext(this.getApplicationContext())` seja chamada da atividade principal. Para obter mais informações, consulte [Métodos de configuração](https://docs.adobe.com/content/help/pt-BR/mobile-services/android/configuration-android/methods.html).

* Há algumas permissões de usuário ausentes no arquivo AndroidManifest.xml fornecido, necessárias para enviar dados e gravar chamadas de rastreamento offline:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Na sua configuração, se o tempo limite do referenciador estiver definido como `referrerTimeout: 5`, você deve enviar a intenção de instalação em um período de 5 segundos após a instalação e inicialização do aplicativo pela primeira vez para ver as informações do referenciador anexadas à ocorrência de instalação.

   Para testes manuais, aumente o `referrerTimeout` para 10–15 segundos, para que haja tempo suficiente para enviar as informações do referenciador antes que a ocorrência de instalação seja processada.

* É importante executar todas as etapas em [Testar a aquisição via link de publicidade](https://docs.adobe.com/content/help/pt-BR/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) para garantir que você execute o shell `adb` e, em seguida, execute o seguinte:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Você deve executar esses dois comandos separadamente para processar a intenção do referenciador de maneira correta.  Caso contrário, o `adb` evita duas vezes as informações do referenciador e os dados recebidos pelo receptor da transmissão estarão incompletos.
