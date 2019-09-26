---
description: Você pode anexar arquivos de imagens às notificações da Apple. Adicionar componentes visuais pode aumentar significativamente a interação dos usuários com as notificações por push.
seo-description: Você pode anexar arquivos de imagens às notificações da Apple. Adicionar componentes visuais pode aumentar significativamente a interação dos usuários com as notificações por push.
seo-title: Receber notificações por push avançadas
title: Receber notificações por push avançadas
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Receive rich push notifications {#receive-rich-push-notifications}

Você pode anexar arquivos de imagens às notificações da Apple. Adicionar componentes visuais pode aumentar significativamente a interação dos usuários com as notificações por push.

Para receber notificações de push avançadas no seu aplicativo iOS:

1. Implemente as mensagens de push para o aplicativo, completando as etapas em [Mensagens de push](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. Verifique se você pode enviar uma mensagem por push de texto para o seu aplicativo.
1. Adicione uma extensão de serviço de notificação completando as seguintes etapas:

   1. In your Xcode project, select  **[!UICONTROL File]** &gt; **[!UICONTROL New]** &gt; **[!UICONTROL Target]**.
   1. Selecione **[!UICONTROL Extensão do serviço de notificação]**.
   1. Verifique se o arquivo `NotificationService.m` existe.

1. Abra o arquivo `NotificationService.m` e verifique se os seguintes métodos Tipo: objetos existem:

   * Um método para receber um pedido de notificação.
   * Um método para lidar com a expiração da extensão do serviço.

      Para receber notificações por push avançadas, o primeiro método é usado:

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      In this method, you can get the Media URL from  by using the  key. `userInfo``attachment-url` Depois de baixar o arquivo em um diretório local, adicione o caminho local a `bestAttemptContent.attachments`.

      Veja um exemplo do código neste método:

      ```objective-c
      - (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
      self.contentHandler = contentHandler;
      self.bestAttemptContent = [request.content mutableCopy];
         NSDictionary* userInfo = request.content.userInfo;
      if(userInfo[@"attachment-url"]){
         NSURL* url = [[NSURL alloc] initWithString:userInfo[@"attachment-url"]];
         NSURLSessionDownloadTask* task = [[NSURLSession sharedSession] downloadTaskWithURL:url completionHandler:^(NSURL * _Nullable location, NSURLResponse * _Nullable response, NSError * _Nullable error) {
             if(!location){
                 return;
             }
             NSString* tmpDirectory = NSTemporaryDirectory();
             NSString* tmpFilePath = [NSString stringWithFormat:@"file://%@%d%d%@", tmpDirectory, arc4random_uniform(100000),
                                    arc4random_uniform(100000), [url lastPathComponent]];
             NSURL* tmpUrl = [[NSURL alloc] initWithString:tmpFilePath];
             NSError * fileError = nil;
             [[NSFileManager defaultManager] moveItemAtURL:location toURL:tmpUrl error:&amp;fileError];
             if(fileError){
                 return;
             }
             UNNotificationAttachment* attachment = [UNNotificationAttachment attachmentWithIdentifier:@"video" URL:tmpUrl options:nil error:&amp;fileError];
             if(fileError){
                 return;
             }
             self.bestAttemptContent.attachments = @[attachment];
             self.contentHandler(self.bestAttemptContent);
         }];
         [task resume];
       }
      }
      ```


Para obter mais informações sobre notificações por push avançadas com o iOS, consulte [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment).
