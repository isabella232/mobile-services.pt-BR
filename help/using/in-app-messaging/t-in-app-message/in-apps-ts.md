---
description: Estas informações podem ajudar a solucionar problemas com as mensagens no aplicativo.
keywords: mobile
seo-description: Estas informações podem ajudar a solucionar problemas com as mensagens no aplicativo.
seo-title: Resolução de problemas nas mensagens no aplicativo
solution: Experience Cloud,Analytics
title: Resolução de problemas nas mensagens no aplicativo
topic: Metrics
uuid: 8813e8d8-bb1e-46ad-83cd-98ae68f73ce6
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 58%

---


# Resolução de problemas nas mensagens no aplicativo {#troubleshooting-in-app-messaging}

Estas informações podem ajudar a solucionar problemas com as mensagens no aplicativo.

Se você concluiu todos os requisitos para mensagens no aplicativo, mas as mensagens não aparecem, verifique os seguintes itens:

## Você está inserindo a nova configuração e o novo SDK no aplicativo?

* Verifique se a versão do SDK é a 4.2 ou superior. Verifique também se foi configurado corretamente.

* Verifique se há uma seção de [Mensagens](/help/using/in-app-messaging/in-app-messaging.md) na sua configuração (o arquivo JSON baixado) ou um terminal remoto de mensagens, para serem recuperados do gerenciamento dinâmico de tags.

## Minha mensagem em tela cheia no Android não é exibida. Estou usando o SDK correto, a configuração e meus acionadores estão sendo atendidos.

Você atualizou o arquivo de manifesto para definir a atividade em tela cheia?

## Minha mensagem de notificação local no Android não está funcionando.

Verifique se o receptor da transmissão de notificação local esteja declarado no seu manifesto. Para obter mais informações, consulte a etapa 1 em [Mensagens no aplicativo](/help/android/messaging-main/messaging/messaging.md).

## A mensagem foi publicada?

Verifique a exibição de lista na coluna **[!UICONTROL Status]** na página Gerenciar mensagens no aplicativo e verifique se a mensagem está ativa.

## Verifique as configurações *mostrar uma vez*, *mostrar sempre*, *mostrar offline* na página Público.

Verifique se essas configurações estão corretas. Na página Público-alvo, analise as opções na guia **[!UICONTROL Acionador]**, na qual você pode especificar a frequência com que a mensagem é exibida.

## Caso esteja usando um evento de inicialização como acionador...

O acionador só será ativado em uma nova sessão. Para obter informações sobre quando começa uma sessão, consulte  `lifecycleTimeout` no arquivo [ADBMobile JSON config](/help/ios/configuration/json-config/json-config.md).

## Atualizei minha mensagem remotamente mas meu aplicativo ainda exibe a mensagem antiga.

Conclua uma das seguintes tarefas:

* O gerenciamento dinâmico de tags pode levar alguns minutos para atualizar seu terminal com sua nova definição.

   Dê um tempo e tente novamente.

* A configuração só será atualizada em um novo lançamento.

   Se o aplicativo foi reiniciado no tempo limite da sessão do ciclo de vida, sua nova configuração pode não ter sido baixada.

## Minha imagem não se encaixa perfeitamente no espaço fornecido pelo modelo.

O modelo em tela cheia de mensagens no aplicativo oferece suporte à exibição de uma imagem de um servidor remoto (URL da imagem) ou do pacote de aplicativos (Imagem embutida). A imagem deve estar em um formato de imagem padrão, por exemplo, JPG, GIF ou PNG.

Devido ao fato de as telas do dispositivo terem muitas dimensões diferentes, a imagem provavelmente não se encaixará perfeitamente no espaço fornecido pelo modelo. O modelo sempre se concentra em mostrar o centro da imagem e cortar (retrato) ou esmaecer (paisagem) as laterais se a imagem não se ajustar.

Estas são as regras de posicionamento e dimensionamento para cada orientação:

* **Retrato**, onde a imagem é dimensionada para a altura de 195px para telefone, 529px para tablet, centralizada se a largura da imagem for menor que a largura do dispositivo e cortada se a largura da imagem for maior que a largura do dispositivo.

* **Paisagem**, onde a imagem é dimensionada para 100% da altura do dispositivo, a largura é 75% do dispositivo e com um desaparecimento gradual à direita.

   Se tiver problemas com o modelo em tela cheia, você pode baixar e usar o modelo HTML personalizado. O modelo HTML personalizado oferece maior flexibilidade para imagens e permite o controle total do modelo.

## Minhas mensagens não estão refletindo alterações/atualizações que fiz na interface do usuário.

O SDK busca mensagens novas/atualizadas no momento de uma inicialização do ciclo de vida. Isso ocorre somente quando o aplicativo é fechado/colocado em segundo plano para um valor maior que o tempo limite do ciclo de vida e, em seguida, reaberto.

Complete as etapas a seguir:

1. Use o comando Curl no URL das mensagens no arquivo de configuração para verificar se a mensagem remota foi atualizada (por exemplo, `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`)
1. Feche o aplicativo.
1. Aguarde um período que seja maior que o `lifecycleTimeout` no arquivo de configuração.
1. Abra o aplicativo, navegue até o local onde a mensagem deve ser exibida e verifique se ela foi atualizada.