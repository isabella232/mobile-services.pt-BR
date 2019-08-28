---
description: Estas informações podem ajudar a solucionar problemas com as mensagens no aplicativo.
keywords: mobile
seo-description: Estas informações podem ajudar a solucionar problemas com as mensagens no aplicativo.
seo-title: Resolução de problemas nas mensagens no aplicativo
solution: Marketing Cloud, Analytics
title: Resolução de problemas nas mensagens no aplicativo
topic: Métricas
uuid: 8813 e 8 d 8-bb 1 e -46 ad -83 cd -98 ae 68 f 73 ce 6
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting in-app messaging{#troubleshooting-in-app-messaging}

Estas informações podem ajudar a solucionar problemas com as mensagens no aplicativo.

Se você concluiu todos os requisitos para as mensagens no aplicativo, mas as mensagens não forem exibidas, verifique os seguintes itens:

## Você está inserindo a nova configuração e o novo SDK no aplicativo?

* Verifique se a versão do SDK é a 4.2 ou superior. Verifique também se foi configurado corretamente.

* Ensure that you have a [Messaging](/help/using/in-app-messaging/in-app-messaging.md) section in your configuration (the downloaded JSON file) or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## Minha mensagem de tela inteira não está aparecendo no Android. Estou usando o SDK correto e a configuração certa, mas meus acionadores não estão funcionando.

Você atualizou seu arquivo de manifesto para definir a atividade de tela inteira?

## Minha mensagem de notificação local no Android não está funcionando.

Verifique se o receptor da transmissão de notificação local esteja declarado no seu manifesto. For more information, see step #1 in [In-app messaging](/help/android/messaging-main/messaging/messaging.md).

## A mensagem foi publicada?

Verifique a exibição de lista na coluna **[!UICONTROL Status]** na página Gerenciar mensagens no aplicativo e verifique se a mensagem está ativa.

## Observe *mostrar uma vez*, *mostrar sempre*, *mostrar* configurações offline na página Público-alvo.

Verifique se essas configurações estão corretas. Na página Público-alvo, analise as opções na guia **Acionador**, na qual você pode especificar a frequência com que a mensagem é exibida.

## Caso esteja usando um evento de inicialização como acionador...

O acionador só será ativado em uma nova sessão. Para obter informações sobre quando uma sessão começa, consulte `lifecycleTimeout` no arquivo [de configuração](/help/ios/configuration/json-config/json-config.md) JSON do adbmobile.

## Atualizei minha mensagem remotamente, mas meu aplicativo ainda exibe a mensagem antiga.

Conclua uma das seguintes tarefas:

* O gerenciamento dinâmico de tags pode levar alguns minutos para atualizar seu terminal com a nova definição.

   Espere um pouco e tente novamente.

* A configuração só será atualizada em um novo lançamento.

   Se o aplicativo tiver sido reiniciado dentro do tempo limite da sessão do ciclo de vida, é possível que a nova configuração não tenha sido baixada.

## Minha imagem não se encaixa perfeitamente no espaço fornecido pelo modelo.

O modelo em tela cheia das mensagens no aplicativo é compatível com a exibição de imagens de um servidor remoto (URL da imagem) ou do conjunto de aplicativos (Imagem embutida). A imagem deve estar em um formato padrão, por exemplo, JPG, GIF ou PNG.

Como as telas dos dispositivos podem ter muitas dimensões diferentes, a imagem provavelmente não se encaixará perfeitamente no espaço fornecido pelo modelo. O modelo sempre se concentra em mostrar o centro da imagem e cortar (retrato) ou esconder (paisagem) as laterais se a imagem não couber.

Estas são as regras de posicionamento e dimensionamento para cada orientação:

* **Retrato**, no qual a imagem é dimensionada para a altura de 195px para telefones, 529px para tablets, centralizada se a largura da imagem for menor que a largura do dispositivo e cortada se a largura da imagem for maior que a largura do dispositivo.

* **Paisagem**, na qual a imagem é dimensionada para 100% da altura do dispositivo, 75% da largura do dispositivo e com um desvanecimento gradual à direita.

   Se tiver problemas com o modelo em tela cheia, é possível baixar e usar o modelo de HTML personalizado. O modelo HTML personalizado proporciona maior flexibilidade para imagens e permite controlar totalmente o modelo.

## As minhas mensagens não estão refletindo as alterações/atualizações que fiz na interface do usuário.

O SDK recupera as mensagens novas/atualizadas no momento da inicialização de um ciclo de vida. Isso ocorre apenas quando o aplicativo é fechado/funciona em segundo plano por um tempo mais longo do que o tempo limite do ciclo de vida e, em seguida, é reaberto.

Complete as etapas a seguir:

1. Ondula o URL da mensagem em seu arquivo de configuração para verificar se a mensagem remota foi atualizada (por exemplo, `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`)
1. Feche o aplicativo.
1. Wait for a time period that is longer than the `lifecycleTimeout` in the config file.
1. Abra o aplicativo, navegue até o local onde a mensagem deve ser exibida e verifique se ela foi atualizada.