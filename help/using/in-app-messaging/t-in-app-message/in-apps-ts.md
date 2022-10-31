---
description: Estas informações podem ajudar a solucionar problemas com as mensagens no aplicativo.
keywords: dispositivos móveis
solution: Experience Cloud Services,Analytics
title: Resolução de problemas nas mensagens no aplicativo
topic-fix: Metrics
uuid: 8813e8d8-bb1e-46ad-83cd-98ae68f73ce6
exl-id: 6be5beef-3bde-49f8-9ec0-c5d32bd43045
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 100%

---

# Resolução de problemas nas mensagens no aplicativo {#troubleshooting-in-app-messaging}

{#eol}

Estas informações podem ajudar a solucionar problemas com as mensagens no aplicativo.

Se você concluiu todos os requisitos para mensagens no aplicativo, mas as mensagens não são exibidas, verifique os seguintes itens:

## Você está inserindo a nova configuração e o novo SDK no aplicativo?

* Verifique se a versão do SDK é a 4.2 ou superior. Verifique também se foi configurado corretamente.

* Verifique se há uma seção de [Mensagens](/help/using/in-app-messaging/in-app-messaging.md) na sua configuração (o arquivo JSON baixado) ou um terminal remoto de mensagens, para serem recuperados do gerenciamento dinâmico de tags.

## Minha mensagem em tela cheia no Android não é exibida. Estou usando o SDK correto, a configuração e meus acionadores estão sendo atendidos.

Você atualizou o arquivo de manifesto para definir a atividade em tela cheia?

## Minha mensagem de notificação local no Android não está funcionando.

Verifique se o receptor da transmissão de notificação local esteja declarado no seu manifesto.

## A mensagem foi publicada?

Verifique a exibição de lista na coluna **[!UICONTROL Status]** na página Gerenciar mensagens no aplicativo e verifique se a mensagem está ativa.

## Verifique as configurações *mostrar uma vez*, *mostrar sempre*, *mostrar offline* na página Público.

Verifique se essas configurações estão corretas. Na página Público-alvo, analise as opções na guia **[!UICONTROL Acionador]**, na qual você pode especificar a frequência com que a mensagem é exibida.

## Caso esteja usando um evento de inicialização como acionador...

O acionador só será ativado em uma nova sessão.

## Atualizei minha mensagem remotamente mas meu aplicativo ainda exibe a mensagem antiga.

Conclua uma das seguintes tarefas:

* O gerenciamento dinâmico de tags pode levar alguns minutos para atualizar seu terminal com a nova definição.

   Dê um tempo e tente novamente.

* A configuração só será atualizada em um novo lançamento.

   Se o aplicativo tiver sido reiniciado dentro do tempo limite da sessão do ciclo de vida, é possível que a nova configuração não tenha sido baixada.

## Minha imagem não se encaixa perfeitamente no espaço fornecido pelo modelo.

O modelo em tela cheia de mensagens no aplicativo é compatível com a exibição de uma imagem de um servidor remoto (URL da imagem) ou do conjunto de aplicativos (Imagem empacotada). A imagem deve estar em um formato padrão, por exemplo, JPG, GIF ou PNG.

Devido ao fato de as telas do dispositivo terem muitas dimensões diferentes, a imagem provavelmente não se encaixará perfeitamente no espaço fornecido pelo modelo. O modelo sempre se concentra em mostrar o centro da imagem e cortar (retrato) ou esmaecer (paisagem) as laterais se a imagem não se ajustar.

Estas são as regras de posicionamento e dimensionamento para cada orientação:

* **Retrato**, onde a imagem é dimensionada para a altura de 195px para celular, 529px para tablet, centralizada se a largura da imagem for menor que a largura do dispositivo e cortada se a largura da imagem for maior que a largura do dispositivo.

* **Paisagem**, onde a imagem é dimensionada para 100% da altura do dispositivo, a largura é 75% do dispositivo e com um esmaecimento gradual à direita.

   Se tiver problemas com o modelo em tela cheia, você pode baixar e usar o modelo HTML personalizado. O modelo HTML personalizado oferece maior flexibilidade para imagens e permite controle total do modelo.

## Minhas mensagens não estão refletindo as alterações/atualizações que fiz na interface do usuário.

O SDK busca mensagens novas/atualizadas no momento de uma inicialização do ciclo de vida. Isso ocorre somente quando o aplicativo é fechado/colocado em segundo plano para um valor maior que o tempo limite do ciclo de vida e, em seguida, reaberto.

Complete as etapas a seguir:

1. Use o comando Curl no URL das mensagens no arquivo de configuração para verificar se a mensagem remota foi atualizada (por exemplo, `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`)
1. Feche o aplicativo.
1. Aguarde um período que seja maior que o `lifecycleTimeout` no arquivo de configuração.
1. Abra o aplicativo, navegue até o local onde a mensagem deve ser exibida e verifique se ela foi atualizada.
