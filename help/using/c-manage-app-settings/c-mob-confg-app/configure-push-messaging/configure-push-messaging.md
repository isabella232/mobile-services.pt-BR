---
description: Você pode usar estas informações para ajudar a configurar as opções de Serviços de push na página Gerenciar configurações do aplicativo, enquanto cria um novo aplicativo ou edita um existente.
keywords: mobile
seo-description: Você pode usar estas informações para ajudar a configurar as opções de Serviços de push na página Gerenciar configurações do aplicativo, enquanto cria um novo aplicativo ou edita um existente.
seo-title: Configuração de mensagens de push
solution: Marketing Cloud,Analytics
title: Configuração de mensagens de push
topic: Métricas
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
translation-type: tm+mt
source-git-commit: 2c85c31d2fa54de26771553a6d349d3101e0048c

---


# Configure push messaging{#configure-push-messaging}

Você pode usar essas informações para ajudá-lo a configurar as opções dos serviços de push na página Gerenciar configurações do aplicativo ao criar um novo aplicativo ou editar um aplicativo existente.

Antes de configurar as mensagens de push, conclua as tarefas de pré-requisito nos [Pré-requisitos para ativar as mensagens](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)de push.

* **Considerações sobre o conjunto de relatórios**

   É possível configurar um aplicativo da app store para a Apple e um para o Google em cada conjunto de relatórios. Se precisar de aplicativos adicionais, por exemplo, um para um ambiente de produção e outro para um ambiente de desenvolvimento, defina um novo aplicativo na app store e um novo conjunto de relatórios para cada ambiente.

>[!IMPORTANT]
>
>Não há suporte para mover seu aplicativo para um novo conjunto de relatórios. Se você migrar para um novo conjunto de relatórios, sua configuração de push pode ser interrompida e as mensagens podem não ser enviadas.

1. Digite as informações nos seguintes campos em **[!UICONTROL Serviços de push]**:

   * Apple

      **[!UICONTROL Chave de privacidade]**

      Browse to and select your valid private key `.p12`, `.key`, or `.pen`.

      >[!IMPORTANT]
      >If the file that you select for the **[!UICONTROL Private Key]** input also contains a certificate, you do not need to specify the certificate.

   * **[!UICONTROL Certificado]**

      Especifique um certificado válido. Essa opção é necessária somente quando a entrada **[!UICONTROL Chave privada]** **não** tem um certificado. Para obter mais informações sobre como obter o certificado SSL e a chave privada, consulte [Configurar o aplicativo para usar o APNS ou o FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

   * Google

      **[!UICONTROL Chave de API]**

      Especifique uma chave de API válida. Para obter mais informações sobre como obter a chave da API, consulte [Configurar o aplicativo para usar o APNS ou o FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

      Para obter mais informações, consulte os seguintes tópicos:

      * [Mensagens de push no Android](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [Mensagens de push no iOS](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. Clique em **[!UICONTROL Salvar]**.
