---
description: Este plug-in permite que você envie chamadas do iOS AppMeasurement do seu projeto PhoneGap.
keywords: phonegap
seo-description: Este plug-in permite que você envie chamadas do iOS AppMeasurement do seu projeto PhoneGap.
seo-title: Plug-in PhoneGap
solution: Experience Cloud,Analytics
title: Plug-in PhoneGap
topic: Developer and implementation
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '327'
ht-degree: 100%

---


# Plug-in PhoneGap {#phonegap-plug-in}

Este plug-in permite que você envie chamadas do iOS AppMeasurement do seu projeto PhoneGap.

## Nova versão do Adobe Experience Platform Mobile SDK

Procurando informações e documentação relacionadas ao Adobe Experience Platform Mobile SDK? Clique [aqui](https://aep-sdks.gitbook.io/docs/) para obter a documentação mais recente.

Em setembro de 2018, lançamos uma nova versão principal do SDK. Esses novos Adobe Experience Platform Mobile SDKs podem ser configurados por meio do [Experience Platform Launch](https://www.adobe.com/br/experience-platform/launch.html).

* Para começar, acesse o Adobe Experience Platform Launch.
* Para ver o conteúdo dos repositórios SDK da Experience Platform, acesse [Github: SDKs da Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Criar um projeto PhoneGap

Para criar um projeto PhoneGap, consulte [PhoneGap](https://helpx.adobe.com/br/experience-manager/6-4/mobile/using/phonegap.html).

## Instalar o plug-in usando npm: {#section_43229E57C16944C0B51531CB92089189}

1. Execute o seguinte comando:

   ```
   cordova plugin add adobe-mobile-services
   ```

## Instalar o plug-in manualmente  {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### Incluir a biblioteca do AppMeasurement

Para incluir AppMeasurement:

1. Arraste `ADBMobile_PhoneGap.h` e `ADBMobile_PhoneGap.m` para a pasta **[!UICONTROL Plugins]** no seu projeto Xcode.
1. Conclua as seguintes configurações:

   1. Selecione **[!UICONTROL Copiar itens na pasta do grupo de destino (se necessário)]**.
   1. Selecione os destinos nos quais você deseja usar o código de AppMeasurement.

1. Arraste `ADB_Helper.js` para a pasta `www` no seu projeto.
1. Na pasta `res/xml`, abra `config.xml` e registre um novo plug-in, adicionando o seguinte:

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### Adicionar permissões do aplicativo

A biblioteca do AppMeasurement requer o seguinte:

1. Abra o Xcode IDE e o seu aplicativo.
1. Arraste a pasta **[!UICONTROL Adobe Mobile]** para o seu projeto Xcode e conclua as seguintes configurações:

   1. Selecione **[!UICONTROL Copiar itens na pasta do grupo de destino (se necessário)]**.
   1. Selecione **[!UICONTROL Criar grupos para qualquer pasta adicionada]**.
   1. Selecione os destinos nos quais você deseja usar o código de AppMeasurement e clique em **[!UICONTROL Concluir]**.

   ![](assets/xcode-settings.png){width=&quot;672&quot;}

1. Na guia **[!UICONTROL Criar fases]** do destino do seu projeto, expanda a seção **[!UICONTROL Link binário com bibliotecas]** e adicione as seguintes bibliotecas:

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Verifique se o aplicativo foi criado sem erros inesperados.

## Implementar o rastreamento personalizado {#section_FD102B3CDAA4492FB04E56BF17E28663}

Nos arquivos `html` nos quais você deseja usar o rastreamento, adicione o código a seguir na guia `<head>`:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

