---
description: Estas informações podem ajudar a solucionar problemas com as mensagens de push.
keywords: dispositivos móveis
solution: Experience Cloud Services,Analytics
title: Solucionar problemas de mensagens de push
topic-fix: Metrics
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
exl-id: 56feb8e1-e196-4b70-8240-6e41581ca602
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 100%

---

# Solucionar problemas de mensagens por push {#troubleshooting-push-messaging}

{#eol}

Estas informações podem ajudar a solucionar problemas com as mensagens de push.

## Por que podem ocorrer atrasos no envio das mensagens de push?

Os seguintes tipos de atrasos podem estar associados a mensagens de push para os Mobile Services:

* **Aguardar as ocorrências do Analytics**

   Todo conjunto de relatórios possui uma configuração que determina quando processar as ocorrências que chegam do Analytics. O padrão é a cada 1 hora.

   O processamento atual de ocorrências do Analytics pode levar até 30 minutos, embora normalmente demore de 15 a 20 minutos. Por exemplo, um conjunto de relatórios processa ocorrências a cada hora. Quando você considera o tempo de processamento necessário de 30 minutos no máximo, pode levar até 90 minutos para que uma ocorrência recebida esteja disponível para uma mensagem de push. Se um usuário inicializasse o aplicativo às 9h01, a ocorrência apareceria na interface do usuário do Mobile Services como um novo usuário único entre 10h15 e 10h30.

* **Aguardando o serviço de push**

   O serviço de push (APNS ou GCM) pode não enviar imediatamente a mensagem. Embora seja incomum, houve ocorrências de tempos de espera de 5 a 10 minutos. É possível verificar se a mensagem de push foi enviada ao serviço de push na exibição **[!UICONTROL Relatório]** da mensagem de push, localizando a mensagem na tabela **[!UICONTROL Histórico de mensagens]** e verificando a contagem de **[!UICONTROL Publicado]**.

   >[!TIP]
   >
   >Os serviços de push não garantem que uma mensagem será enviada. Para obter mais informações sobre a confiabilidade dos serviços, consulte a documentação apropriada:
   >
   >* **APNS**: [Qualidade do serviço](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   >* **FCM**: [Tempo de vida de uma mensagem](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)


## Por que minha chave de API GCM do Android é inválida?

* **Chave de API inválida**

   Sua chave de API pode estar inválida pelos seguintes motivos:

   * A chave de API fornecida não é uma chave de servidor com o valor correto da chave de API GCM.
   * A chave do servidor permitiu os IPs e está impedindo os servidores da Adobe de enviarem uma mensagem de push.

* **Determine a validade da chave de API**

   Para determinar a validade da sua chave de API, execute o seguinte comando:

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   Um código de status 401 HTTP retornado significa que sua chave de API é inválida. Caso contrário, você verá algo semelhante a isto:

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   Também é possível verificar a validade de um token de registro, substituindo `"ABC"` pelo token.

## Por que meu certificado APNS não está funcionando?

Seu certificado APNS pode estar inválido pelos seguintes motivos:

* Você pode estar usando um certificado de sandbox em vez do certificado de produção.
* Você está usando um novo certificado de produção/sandbox que não é compatível.
* Você está usando um arquivo `.p8` em vez de `.p12`.

## Resolução de falhas na mensagem de push

O exemplo a seguir ilustra como você pode resolver uma falha de envio ao usar um VRS.

O seguinte cliente tem dois aplicativos iOS:

* Nome do aplicativo: PhotoShop_app_iOS
   * RSID principal: AllAdobe PhotoShop_apps
   * VRSID: PhotoShop_iOS_app_SF
   * Segmento de definição de VRSID: `a.appid contains "PhotoShop_iOS_app_SF"`
* Nome do aplicativo: PhotoShop_app_iOS
   * RSID principal: AllAdobe PhotoShop_apps
   * RSID: PhotoShop_iOS_app_LA
   * Segmento de definição de VRSID: `a.os contains "iOS"`

Neste exemplo, se um colaborador do Photoshop enviar uma mensagem por push para o aplicativo *PhotoShop_iOS_app_SF*, todos os usuários do *aplicativo PhotoShop_iOS_app_SF* receberão a mensagem como esperado. Porém, se o colaborador enviar uma mensagem para o aplicativo *PhotoShop_iOS_app_LA*, porque o segmento de definição do VRSID está incorreto (`iOS` em vez de `a.os contains "PhotoShop_iOS_app_LA"`), a mensagem será enviada para **todos** os usuários do iOS em *AllAdobe PhotoShop_apps*. A mensagem não deixará de ser enviada para os usuários do *PhotoShop_iOS_app_LA*, mas também incluirá nas listas de bloqueio as IDs de push dos usuários do *PhotoShop_iOS_app_SF*, porque o aplicativo *PhotoShop_iOS_app_SF* tem um certificado diferente. Se o segmento tivesse sido definido como `a.os contains "PhotoShop_iOS_app_LA"`, a mensagem por push teria sido enviada apenas para os usuários do *PhotoShop_iOS_app_LA*.

Se aprovados com o certificado de push do *PhotoShop_IOS_app_LA*, os identificadores de push para o *PhotoShop_iOS_app_SF* voltam como `invalid`.

>[!CAUTION]
>
>Uma vez criada uma mensagem por push para um aplicativo que esteja usando um VRS e após clicar em **[!UICONTROL Salvar e enviar]**, será exibido um alerta para lembrar que cada aplicativo listado **deve** ter um certificado válido. Caso cada aplicativo **não** tenha um certificado válido, os segmentos de público-alvo talvez sejam adicionados à lista de bloqueios indefinidamente e você não pode mais enviar futuras mensagens de push para os usuários afetados. Para obter mais informações sobre segmentos de público, consulte [Público: definir e configurar as opções de público para mensagens por push](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).
