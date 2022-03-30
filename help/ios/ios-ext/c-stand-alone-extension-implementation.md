---
description: A partir do iOS 10, a Apple permitirá que você crie uma extensão chamada de extensão independente que pode ser distribuída sem um aplicativo contêiner. Com essa extensão, você não precisa de um grupo de aplicativos, pois não há um aplicativo contêiner com o qual compartilhar dados.
solution: Experience Cloud Services,Analytics
title: Implementação de extensão independente
topic-fix: Developer and implementation
uuid: 9b47f082-b78f-4611-968d-014c32ede6bc
exl-id: b51247b6-c4ba-4a00-9ba0-1824450ac067
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 100%

---

# Implementação de extensão independente {#stand-alone-extension-implementation}

A partir do iOS 10, a Apple permitirá que você crie uma extensão chamada de extensão independente que pode ser distribuída sem um aplicativo contêiner. Com essa extensão, você não precisa de um grupo de aplicativos, pois não há um aplicativo contêiner com o qual compartilhar dados.

>[!IMPORTANT]
>
>Para usar extensões independentes, você deve ter o Mobile SDK versão 4.13.0 ou posterior.

## Configurar sua extensão independente para usar com o SDK {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

Para configurar sua extensão independente:

1. Certifique-se de que o arquivo `ADBMobileConfig.json` é um membro do destino da sua extensão.
1. Vincule as seguintes bibliotecas e estruturas:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. No controlador de exibição principal da sua extensão, defina o tipo de extensão para `ADBMobileAppExtensionTypeStandAlone` no SDK antes de completar qualquer atividade relacionada ao SDK.

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. Verifique se o aplicativo foi criado sem erros inesperados.

## Observações adicionais {#section_1C9A55E2309A44BF842310F735702B3D}

Estas são algumas informações adicionais:

* Um valor de dados de contexto adicional, `a.RunMode`, foi adicionado para indicar se os dados são provenientes do aplicativo contêiner ou da extensão:

   * `a.RunMode = Application`

      Esse valor significa que a ocorrência veio do aplicativo contêiner.
   * `a.RunMode = Extension`

      Esse valor significa que a ocorrência veio da extensão.

* Nenhuma chamada de ciclo de vida é acionada nos aplicativos de extensão iOS.
