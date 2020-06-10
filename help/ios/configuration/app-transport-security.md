---
description: Essas informações o ajudarão a trabalhar com o App Transport Security (ATS), um novo conjunto de requisitos de segurança do iOS 9.
seo-description: Essas informações o ajudarão a trabalhar com o App Transport Security (ATS), um novo conjunto de requisitos de segurança do iOS 9.
seo-title: App Transport Security
solution: Marketing Cloud,Analytics
title: App Transport Security
topic: Developer and implementation
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
translation-type: tm+mt
source-git-commit: e6af295ddc5fea2a3e649b659894e6c6123a3457
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 84%

---


# App Transport Security {#app-transport-security}

Essas informações o ajudarão a trabalhar com o App Transport Security (ATS), um novo conjunto de requisitos de segurança do iOS 9.

Começando pelo iOS 9, a Apple apresentou o App Transport Security, um conjunto de requisitos que cumpre as práticas recomendadas para conexões seguras. Para obter mais informações, consulte *NSAppTransportSecurity* em [Information Property List Key Reference](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/).

Para o Adobe Mobile SDK versão 4.7 ou posteriores funcionar de maneira simples com o ATS, use a opção de habilitar SSL na página Gerenciar configurações do aplicativo. Para obter mais informações, consulte [Gerenciar configurações do aplicativo](/help/using/c-manage-app-settings/c-manage-app-settings.md) ou [Configuração JSON do ADBMobile](/help/ios/configuration/json-config/json-config.md).

No Adobe Mobile Services, ao selecionar a opção **[!UICONTROL Usar HTTPS]** na página Gerenciar configurações do aplicativo, todas as ocorrências do Analytics, do Audience Manager, do Target e do Adobe Experience Platform Identity Services são enviadas por meio de HTTPS.

Como alternativa, você pode colocar os seguintes servidores na lista &quot;permitida&quot;:

| Produto | Instruções |
|--- |--- |
| Analytics | Para permitir o servidor do Analytics, adicione o domínio do servidor de rastreamento ao arquivo info.plist como um domínio de exceção para ATS.  O domínio do servidor de rastreamento pode ser encontrado na seção Analytics do arquivo `ADBMobileConfig.json` ou na seção Analytics na página Gerenciar as configurações do aplicativo. |
| Audience Manager | O domínio do Audience Manager é encontrado na propriedade de servidor do objeto audienceManager no arquivo `ADBMobileConfig.json`.  Se estiver usando o Audience Manager no seu aplicativo e o SSL não estiver habilitado, adicione este servidor como um domínio de exceção para o ATS no arquivo `Info.plist`. |
| Target | É possível adicionar o terminal Target ao arquivo Info.plist como um domínio de exceção para ATS.  Para encontrar o terminal do Target, encontre `clientCodeproperty` no objeto de destino do arquivo `ADBMobileConfig.json`. Seu terminal será `https://{clientCode}.tt.omtrdc.net`.  Por exemplo, se o `clientCodeproperty` for `“myCompany”`, o terminal será `https://myCompany.tt.omtrdc.net`. |
| Adobe Experience Platform Identity Service | É possível adicionar o servidor da Experience Cloud como um domínio de exceção para ATS em seu arquivo `Info.plist`. Este domínio é `dpm.demdex.net`. |
| Mobile Services: aquisição | Allow the Acquisition server as an exception domain for ATS in your  `Info.plist` file. Este domínio é `c00.adobe.com`. |
| Mobile Services: Mensagens no aplicativo | Se estiver usando mensagens no aplicativo, talvez seja necessário adicionar entradas no domínio de exceção para ATS para cada URL que você usa que não seja HTTPS. Esta lista inclui imagens hospedadas e qualquer URL incorporado no HTML da mensagem em tela cheia personalizada.  Para obter mais detalhes sobre como configurar o domínio de exceções em um arquivo `info.plist`, consulte a linha *NSExceptionDomains* em *Tabela 2: chaves principais do dicionário App Transport Security*. Consulte também *Tabela 3: Chaves do dicionário Domínios de exceção* em [Information Property List Key Reference](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/). |

>[!TIP]
>
>Essas considerações afetam as conexões feitas pelo Adobe Mobile SDK e não impactam a exibição na Web nem outras conexões feitas pelo aplicativo.

