---
description: Essas informações o ajudarão a trabalhar com o App Transport Security (ATS), um novo conjunto de requisitos de segurança do iOS 9.
seo-description: Essas informações o ajudarão a trabalhar com o App Transport Security (ATS), um novo conjunto de requisitos de segurança do iOS 9.
seo-title: App Transport Security
solution: Marketing Cloud, Analytics
title: App Transport Security
topic: Desenvolvedor e implementação
uuid: e 9 ee 13 cf -9802-492 e -8 b 11-95 f 028 e 34 e 61
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# App Transport Security {#app-transport-security}

Essas informações o ajudarão a trabalhar com o App Transport Security (ATS), um novo conjunto de requisitos de segurança do iOS 9.

Começando pelo iOS 9, a Apple apresentou o App Transport Security, um conjunto de requisitos que cumpre as práticas recomendadas para conexões seguras. Para obter mais informações, consulte *nsapptransportsecurity* na [Referência de chave da lista de propriedades da informação](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/).

Para o Adobe Mobile SDK versão 4.7 ou posteriores funcionar de maneira simples com o ATS, use a opção de habilitar SSL na página Gerenciar configurações do aplicativo. Para obter mais informações, consulte [Gerenciar configurações do aplicativo](/help/using/c-manage-app-settings/c-manage-app-settings.md) ou [configuração JSON do adbmobile](/help/ios/configuration/json-config/json-config.md).

In Adobe Mobile Services, by selecting the **[!UICONTROL Use HTTPS]** option in the Manage App Settings page, all hits from Analytics, Audience Manager, Target, and Adobe Experience Platform Identity Services are sent via HTTPS.

Como alternativa, você pode fazer o serviço de lista de permissões os seguintes servidores:

| Produto | Instruções |
|--- |--- |
| Analytics | Para adicionar o servidor Analytics à lista de permissões, adicione o domínio de servidor de rastreamento ao arquivo info.plist como um domínio de exceção para ATS.  O domínio do servidor de rastreamento pode ser encontrado na seção Analytics do arquivo `ADBMobileConfig.json` ou na seção Analytics na página Gerenciar as configurações do aplicativo. |
| Audience Manager | O domínio do Audience Manager é encontrado na propriedade de servidor do objeto audienceManager no arquivo `ADBMobileConfig.json`.  Se estiver usando o Audience Manager no seu aplicativo e o SSL não estiver habilitado, adicione este servidor como um domínio de exceção para o ATS no arquivo `Info.plist`. |
| Target | É possível adicionar o terminal Target ao arquivo Info.plist como um domínio de exceção para ATS.  Para encontrar o terminal do Target, encontre `clientCodeproperty` no objeto de destino do arquivo `ADBMobileConfig.json`. Your endpoint will be `https://{clientCode}.tt.omtrdc.net`.  For example, if your `clientCodeproperty` is `“myCompany”`, your endpoint will be `https://myCompany.tt.omtrdc.net`. |
| Adobe Experience Platform Identity Service | É possível adicionar o servidor da Experience Cloud como um domínio de exceção para ATS em seu arquivo `Info.plist`. This domain is `dpm.demdex.net`. |
| Mobile Services: aquisição | Inclua o servidor de Aquisição em uma lista de permissões como um domínio de exceção para o ATS no arquivo `Info.plist`. This domain is `c00.adobe.com`. |
| Mobile Services: mensagens no aplicativo | Se você estiver usando mensagens no aplicativo, talvez seja necessário adicionar entradas no domínio de exceção para ATS para cada URL utilizada que não for HTTPS. Esta lista inclui imagens hospedadas e qualquer URL incorporado no HTML da mensagem em tela cheia personalizada.  Para obter mais detalhes sobre como configurar o domínio de exceções em um `info.plist` arquivo, consulte a linha *nsexemariondomains* na *Tabela 2: Chaves primárias do dicionário App Transport Security*. Consulte *também as teclas* dicionário de domínios da Tabela 3 em Referência da chave de lista da propriedade [de informações](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/). |

>[!TIP]
>
>Essas considerações afetam as conexões feitas pelo SDK do Adobe Mobile e não afetam a visualização da Web ou outras conexões feitas pelo aplicativo.

