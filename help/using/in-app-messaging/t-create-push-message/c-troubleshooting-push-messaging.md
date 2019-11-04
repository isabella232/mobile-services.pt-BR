---
description: Estas informações podem ajudar a solucionar problemas com as mensagens de push.
keywords: dispositivos móveis
seo-description: Estas informações podem ajudar a solucionar problemas com as mensagens de push.
seo-title: Solucionar problemas de mensagens de push
solution: Experience Cloud,Analytics
title: Solucionar problemas de mensagens de push
topic: Métricas
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
translation-type: ht
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Solucionar problemas de mensagens por push{#troubleshooting-push-messaging}

Estas informações podem ajudar a solucionar problemas com as mensagens de push.

## Por que podem ocorrer atrasos no envio das mensagens de push?

Os seguintes tipos de atrasos podem estar associados a mensagens de push para os Mobile Services:

* **Aguardar as ocorrências do Analytics**

   Todo conjunto de relatórios possui uma configuração que determina quando processar as ocorrências que chegam do Analytics. O padrão é a cada 1 hora.

   O processamento atual de ocorrências do Analytics pode levar até 30 minutos, embora normalmente demore de 15 a 20 minutos. Por exemplo, um conjunto de relatórios processa ocorrências a cada hora. Quando você considera o tempo de processamento necessário de 30 minutos (no máximo), talvez demore até 90 minutos para que uma ocorrência recebida esteja disponível para uma mensagem de push. Se um usuário inicializasse o aplicativo às 9h01, a ocorrência apareceria na interface do usuário do Mobile Services como um novo usuário exclusivo entre 10h15 e 10h30.

* **Aguardar o serviço de push**

   O serviço de push (APNS ou GCM) talvez não envie a mensagem imediatamente. Embora seja incomum, houve ocorrências de tempos de espera de 5 a 10 minutos. É possível verificar se a mensagem de push foi enviada ao serviço de push na exibição **[!UICONTROL Relatório]** da mensagem de push, localizando a mensagem na tabela **[!UICONTROL Histórico de mensagens]** e verificando a contagem de **[!UICONTROL Publicado]**.

   >[!TIP]
   >
   >Essa contagem é o número de envios bem-sucedidos para os serviços de push. Os serviços de push não garantem que uma mensagem será enviada.

   Para obter mais informações sobre a confiabilidade do serviço, consulte:

   * [Qualidade do serviço](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [Tempo de vida de uma mensagem](https://developers.google.com/cloud-messaging/concept-options#lifetime).

## Por que minha chave de API GCM do Android é inválida?

* **Chave de API inválida**

   A chave de API pode ser inválida pelos seguintes motivos:

   * A chave de API que você forneceu não é uma chave de servidor com o valor de chave de API GCM correto.
   * A chave do servidor incluiu os IPs em uma lista de permissões e está impedindo os servidores da Adobe de enviarem uma mensagem de push.

* **Determinar a validade da chave de API**

   Para determinar a validade da chave de API, execute o seguinte comando:

   **Android**

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   Um código do status 401 HTTP retornado significa que a chave de API é inválida. Caso contrário, você verá algo semelhante a isto:

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   Também é possível verificar a validade de um token de registro, substituindo `"ABC"` pelo token.

## Por que meu certificado APNS não está funcionando?

O certificado APNS pode ser inválido pelos seguintes motivos:

* Você pode usar um certificado de sandbox em vez do certificado de produção.
* Você está usando um novo certificado de produção/sandbox que não é suportado.
* Você está usando um arquivo `.p8` em vez de `.p12`.

## Resolução de falhas na mensagem de push

**Um exemplo**

O exemplo a seguir ilustra como você pode resolver uma falha de push ao usar um VRS.

O seguinte cliente tem dois aplicativos iOS:

* Nome do aplicativo: PhotoShop_app_iOS
   * RSID principal: AllAdobe PhotoShop_apps
   * VRSID: PhotoShop_iOS_app_SF
   * Segmento de definição de VRSID: `a.appid contains “PhotoShop_iOS_app_SF”`
* Nome do aplicativo: PhotoShop_app_iOS
   * RSID principal: AllAdobe PhotoShop_apps
   * RSID: PhotoShop_iOS_app_LA
   * Segmento de definição de VRSID: `a.os contains “iOS”`

Neste exemplo, se um colaborador do Photoshop enviar uma mensagem por push para o aplicativo *PhotoShop_iOS_app_SF*, todos os usuários do *aplicativo PhotoShop_iOS_app_SF* receberão a mensagem como esperado. Porém, se o colaborador enviar uma mensagem para o aplicativo *PhotoShop_app_LA*, porque o segmento de definição do VRSID está incorreto (`iOS` em vez de `a.os contains "PhotoShop_iOS_app_LA"`), a mensagem será enviada para **todos** os usuários do iOS em *AllAdobe PhotoShop_apps*. A mensagem não deixará de ser enviada para os usuários do *PhotoShop_iOS_app_LA*, mas também incluirá na blacklist as IDs de push dos usuários do *PhotoShop_iOS_app_SF*, porque o aplicativo *PhotoShop_iOS_app_SF* tem um certificado diferente. Se o segmento tivesse sido definido como `a.os contains “PhotoShop_iOS_app_LA”`, a mensagem por push teria sido enviada apenas para os usuários do *PhotoShop_iOS_app_LA*.

Se aprovados com o certificado de push do *PhotoShop_IOS_app_LA*, os identificadores de push para o *PhotoShop_iOS_app_SF* voltam como `invalid`.

>[!CAUTION]
>
>Uma vez criada uma mensagem por push para um aplicativo que esteja usando um VRS e após clicar em **[!UICONTROL Salvar e enviar]**, será exibido um alerta para lembrar que cada aplicativo listado **deve** ter um certificado válido. Caso cada aplicativo **não** tenha um certificado válido, os segmentos de público-alvo talvez sejam adicionados à lista negra indefinidamente e você não pode mais enviar futuras mensagens de push para os usuários afetados. Para obter mais informações sobre segmentos de público, consulte [Público: definir e configurar as opções de público para mensagens por push](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).
