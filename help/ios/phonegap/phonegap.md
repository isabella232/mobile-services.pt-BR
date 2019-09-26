---
description: Este plug-in permite que você envie chamadas do iOS AppMeasurement do seu projeto PhoneGap.
keywords: phonegap
seo-description: Este plug-in permite que você envie chamadas do iOS AppMeasurement do seu projeto PhoneGap.
seo-title: Plug-in PhoneGap
solution: Marketing Cloud,Analytics
title: Plug-in PhoneGap
topic: Desenvolvedor e implementação
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# PhoneGap plug-in{#phonegap-plug-in}

Este plug-in permite que você envie chamadas do iOS AppMeasurement do seu projeto PhoneGap.

## Nova versão do SDK da Adobe Experience Cloud

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para acessar a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para começar, acesse o Launch.
* Para ver o conteúdo dos repositórios do Experience Platform SDK, acesse [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Para obter mais informações, consulte [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

Para criar um projeto PhoneGap, consulte [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## Instalar o plug-in usando npm: {#section_43229E57C16944C0B51531CB92089189}

1. Execute o seguinte comando:

   ```
   cordova plugin add adobe-mobile-services
   ```

## Instalar o plug-in manualmente {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### Incluir a biblioteca do AppMeasurement

Para incluir AppMeasurement:

1. Drag `ADBMobile_PhoneGap.h` and  `ADBMobile_PhoneGap.m` into the **[!UICONTROL Plugins]** folder in your Xcode project.
1. Conclua as seguintes configurações:

   1. Selecione **[!UICONTROL Copiar itens na pasta do grupo de destino (se necessário)]**.
   1. Selecione os destinos nos quais você deseja usar o código de AppMeasurement.

1. Drag `ADB_Helper.js` into the `www` folder in your project.
1. In the `res/xml` folder, open `config.xml` and register an new plugin by adding the following:

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### Adicionar permissões de aplicativo

A biblioteca AppMeasurement exige o seguinte:

1. Abra o Xcode IDE e o seu aplicativo.
1. Arraste a pasta **[!UICONTROL Adobe Mobile]no seu projeto Xcode e conclua as seguintes configurações:**

   1. Selecione **[!UICONTROL Copiar itens na pasta do grupo de destino (se necessário)]**.
   1. Selecione **[!UICONTROL Criar grupos para qualquer pasta adicionada]**.
   1. Selecione os destinos nos quais você deseja usar o código de AppMeasurement e clique em **[!UICONTROL Concluir]**.
   ![](assets/xcode-settings.png){width="672"}

1. Na guia **[!UICONTROL Criar fases]** do destino do seu projeto, expanda a seção **Link binário com bibliotecas]e adicione as seguintes bibliotecas:[!UICONTROL **

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Verifique se o aplicativo foi criado sem erros inesperados.

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

