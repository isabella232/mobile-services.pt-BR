---
description: A partir do iOS 10, a Apple permitirá a criação de uma extensão chamada de extensão independente, que pode ser distribuída sem um aplicativo contêiner. Com esta extensão, não é necessário ter um grupo de aplicativos, já que não há um aplicativo contêiner com o qual compartilhar os dados.
seo-description: A partir do iOS 10, a Apple permitirá a criação de uma extensão chamada de extensão independente, que pode ser distribuída sem um aplicativo contêiner. Com esta extensão, não é necessário ter um grupo de aplicativos, já que não há um aplicativo contêiner com o qual compartilhar os dados.
seo-title: Implementação de extensão independente
solution: Marketing Cloud, Analytics
title: Implementação de extensão independente
topic: Desenvolvedor e implementação
uuid: 9 b 47 f 082-b 78 f -4611-968 d -014 c 32 ede 6 bc
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Stand-alone extension implementation {#stand-alone-extension-implementation}

A partir do iOS 10, a Apple permitirá a criação de uma extensão chamada de extensão independente, que pode ser distribuída sem um aplicativo contêiner. Com esta extensão, não é necessário ter um grupo de aplicativos, já que não há um aplicativo contêiner com o qual compartilhar os dados.

>[!IMPORTANT]
>
>Para usar extensões independentes, você deve ter o Mobile SDK versão 4.13.0 ou posterior.

## Configurar sua extensão independente para usar com o SDK {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

Para configurar sua extensão independente:

1. Ensure that the `ADBMobileConfig.json` file is a member of your extension's target.
1. Vincule as seguintes bibliotecas e estruturas:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. No controlador de exibição principal da sua extensão, defina o tipo de extensão para `ADBMobileAppExtensionTypeStandAlone` no SDK antes de completar qualquer atividade relacionada ao SDK.

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. Verifique se o aplicativo foi criado sem erros inesperados.

## Additional notes {#section_1C9A55E2309A44BF842310F735702B3D}

Estas são algumas informações adicionais:

* Um valor de dados de contexto adicional, `a.RunMode`, foi adicionado para indicar se os dados são provenientes do aplicativo contêiner ou da extensão:

   * `a.RunMode = Application`

      Esse valor significa que a ocorrência veio do aplicativo contêiner.
   * `a.RunMode = Extension`

      Esse valor significa que a ocorrência veio da extensão.

* Nenhuma chamada de ciclo de vida é acionada em aplicativos de extensão iOS.

