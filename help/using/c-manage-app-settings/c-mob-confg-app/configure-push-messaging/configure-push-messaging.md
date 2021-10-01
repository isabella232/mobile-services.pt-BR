---
description: Você pode usar estas informações para ajudar a configurar as opções de Serviços de push na página Gerenciar configurações do aplicativo, enquanto cria um novo aplicativo ou edita um existente.
keywords: dispositivos móveis
solution: Experience Cloud,Analytics
title: Configurar mensagens por push
topic-fix: Metrics
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
exl-id: d4989c31-2692-4062-8fae-d41c3e3c179b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 100%

---

# Configurar mensagens por push {#configure-push-messaging}

Se estiver criando um novo aplicativo ou editando um existente, você pode usar estas informações para configurar as opções de Serviços por push na página Gerenciar configurações do aplicativo.

Antes de configurar mensagens por push, conclua as tarefas obrigatórias em [Pré-requisitos para habilitar as mensagens por push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md).

* **Considerações sobre o conjunto de relatórios**

   Você pode configurar um aplicativo da app store para a Apple e um para o Google em cada conjunto de relatórios. Se você precisar de aplicativos adicionais, por exemplo, um para um ambiente de produção e outro para um ambiente dev, configure um novo aplicativo da app store e um novo conjunto de relatórios para cada ambiente.

>[!IMPORTANT]
>
>Não é possível mover seu aplicativo para um novo conjunto de relatórios. Se você migrar para um novo conjunto de relatórios, sua configuração de push pode ser interrompida e as mensagens podem não ser enviadas.

1. Digite as informações nos seguintes campos em **[!UICONTROL Serviços de push]**:

   * Apple

      **[!UICONTROL Chave de privacidade]**

      Procure e selecione sua chave privada e válida `.p12`, `.key`, ou `.pen`.

      >[!IMPORTANT]
      >Se o arquivo selecionado para a entrada **[!UICONTROL Chave privada]** também contiver um certificado, não será necessário especificar o certificado.

   * **[!UICONTROL Certificado]**

      Especifique um certificado válido. Essa opção é necessária somente quando a entrada **[!UICONTROL Chave privada]** **não** tem um certificado. Para mais informações sobre como obter o certificado SSL e a chave privada, consulte [Configurar o aplicativo para uso do APNS ou do FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

   * Google

      **[!UICONTROL Chave de API]**

      Especifique uma chave de API válida. Para obter mais informações sobre como obter a chave API, consulte [Configurar o aplicativo para uso do APNS ou do FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

      Para obter mais informações, consulte os seguintes tópicos:

      * [Mensagens por push no Android](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [Mensagens por push no iOS](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. Clique em **[!UICONTROL Salvar]**.
