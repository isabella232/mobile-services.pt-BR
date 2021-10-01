---
description: É possível gerar links de aquisição com códigos de rastreamento exclusivos no Adobe Mobile Services. Quando um usuário baixa e executa um aplicativo da loja de aplicativos da Apple depois de clicar em um link gerado, o SDK coleta e envia automaticamente os dados de aquisição para o Adobe Mobile Services.
solution: Experience Cloud,Analytics
title: Aquisição de aplicativos móveis
topic-fix: Developer and implementation
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
exl-id: a90dcb2f-babb-4c97-b67a-8468925ee5c8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 100%

---

# Aquisição de aplicativos móveis {#mobile-app-acquisition}

É possível gerar links de aquisição com códigos de rastreamento exclusivos no Adobe Mobile Services. Quando um usuário baixa e executa um aplicativo da loja de aplicativos da Apple depois de clicar em um link gerado, o SDK coleta e envia automaticamente os dados de aquisição para o Adobe Mobile Services.

Para usar a Aquisição, você **deve** ter a versão 4.1 ou posterior do SDK.

Os links de aquisição devem ser criados nos Adobe Mobile Services. Para obter mais informações, consulte [Aquisição](/help/using/acquisition-main/acquisition-main.md).

As atualizações nessa seção permitem que o SDK envie dados de aquisição a partir de um link de aquisição.

## Rastreamento da aquisição de aplicativos móveis {#section_CEA30C652AC8470784B8054E299B80FA}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao seu projeto* em [Implementação principal e ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe a biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verifique se o arquivo `ADBMobileConfig.json` contém as configurações de aquisição exigidas:

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   >Se estiver enviando dados para vários conjuntos de relatórios, use as configurações de aquisição (servidor de aquisição e appid) do aplicativo associado ao primeiro conjunto de relatórios na sua lista de IDs de conjuntos de relatórios.

   As configurações `acquisition` são geradas pelo Adobe Mobile Services e não devem ser alteradas. Para obter mais informações sobre como baixar um arquivo `ADBMobileConfig.json` personalizado com as configurações de `acquisition` predefinidas, consulte [Antes de iniciar](/help/ios/getting-started/requirements.md).

Após essas configurações serem ativadas, os dados de aquisição são enviados automaticamente com a chamada de ciclo de vida inicial após a primeira inicialização do aplicativo.

>[!CAUTION]
>
>`referrerTimeout` deve ser definido com um valor maior que 0 para habilitar a aquisição do aplicativo.

## Ativação do aplicativo iOS para links universais

Se você estiver usando Links universais no aplicativo, adicione o domínio Links de marketing da Adobe à lista Domínios associados do aplicativo.

No Xcode, para adicionar seu domínio Adobe Marketing Links à lista Domínios associados:

1. Vá para a meta do projeto e clique na guia **[!UICONTROL Recursos]**.
2. Role para baixo até a seção **[!UICONTROL Domínios associados]** e alterne-a.
3. Adicione uma entrada na lista **[!UICONTROL Domínios]** para seu domínio de Links de marketing a partir do URL de Links de marketing.

Sua entrada será parecida com `applinks:5848561889a02a6996aea62b.c00.adobe.com`.
