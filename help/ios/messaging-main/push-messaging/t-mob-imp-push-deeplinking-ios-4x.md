---
description: Depois de configurar o URL de deep linking na interface do usuário do Adobe Mobile Services, este URL estará na carga de envio com a chave adb_deeplink.
title: Implementar mensagens de push com deep linking
uuid: ee9590fc-8bd3-4111-9221-9011d9edbd84
exl-id: c9ca955c-506f-45fe-82d6-fad2f9a80130
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 96%

---

# Implementar mensagens por push com deep linking {#implement-push-messaging-with-deep-linking}

Depois de configurar o URL de deep linking na interface do usuário do Adobe Mobile Services, este URL estará na carga de envio com a chave `adb_deeplink`.

1. No AppDelegate, você pode recuperar o URL do deep link e lidar com isso sozinho nos seguintes locais:

   * Em `application:didFinishLaunchingWithOptions`:

      Se o aplicativo não estiver sendo executado quando ocorrer um clique por push, você poderá obter a carga de push de `launchOptions` e o URL do deep link estará no dicionário da carga com a chave `adb_deeplink`.

   * Os métodos delegados para Notificação remota

      No aplicativo `didReceiveRemoteNotification:` ou `didReceiveRemoteNotification:fetchCompletionHandler:`, é possível obter o URL acessando o dicionário `userInfo` com a chave `adb_deeplink`.

   * Os métodos delegados para `UNUserNotificationCenter`

      No método `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler:`, é possível obter a carga de push do dicionário `userInfo`, na chave `adb_deeplink`.

Por exemplo:

```objective-c
- (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    NSDictionary *remoteNotification = launchOptions[UIApplicationLaunchOptionsRemoteNotificationKey]; 
    if (remoteNotification && [remoteNotification isKindOfClass:[NSDictionary class]]) { 
        NSString *deeplink = remoteNotification[@"adb_deeplink"]; 
        // handle deep link url 
    }
    return YES; 
} 
  
// app target < iOS 7 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
    // only send the hit if the app is not active 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
} 
  
// app target >= iOS 7 
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler { 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
    ... 
} 
 
// if using UNUserNotificationCenterDelegate and device is running iOS 10 or newer 
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
    if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
        [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
        NSString *deeplink = response.notification.request.content.userInfo[@"adb_deeplink"]; 
        // handle deep link url  
    } 
    ... 
}
```
