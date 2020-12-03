---
description: Estas informações ajudam a solucionar problemas de mensagem de push no aplicativo.
keywords: mobile
seo-description: Estas informações ajudam a solucionar problemas de mensagem de push no aplicativo.
seo-title: Resolução de problemas de mensagens no aplicativo
solution: Experience Cloud,Analytics
title: Resolução de problemas de mensagens no aplicativo
topic: Metrics
uuid: 39c3a21d-92c2-4004-b00f-99b6f91d3696
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 100%

---


# Resolução de problemas de mensagens no aplicativo {#troubleshooting-in-app-messaging}

Estas informações ajudam a solucionar problemas de mensagem de push no aplicativo.

Se você concluiu todos os requisitos para mensagens no aplicativo, mas as mensagens não são exibidas, verifique os seguintes itens:

## Você está inserindo a nova configuração e o novo SDK no aplicativo?

Certifique-se de que há uma seção [Mensagens no aplicativo](/help/android/messaging-main/messaging/messaging.md) na sua configuração (arquivo JSON baixado) ou um terminal remoto de mensagens, para que ele possa ser recuperado do gerenciamento dinâmico de tags.

## Minha mensagem em tela cheia no Android não é exibida. Estou usando o SDK correto, a configuração e meus acionadores estão sendo atendidos.

Você atualizou o arquivo de manifesto para definir a atividade em tela cheia?

## Minha mensagem de notificação local no Android não está funcionando.

Certifique-se de que o destinatário de transmissão de notificação local esteja declarado no manifesto. Para obter mais informações, consulte a etapa 2 em *Habilitar mensagens no aplicativo* em [Mensagens no aplicativo](/help/android/messaging-main/messaging/messaging.md).

## A mensagem foi publicada?

Para verificar se a mensagem é em tempo real, na página Gerenciar mensagens no aplicativo, na coluna **[!UICONTROL Status]**, verifique a lista de mensagens.

## Observe as configurações *mostrar uma vez*, *mostrar sempre* e *mostrar offline* na guia Público-alvo.

Verifique se essas configurações estão definidas do modo como você deseja. Na guia **[!UICONTROL Público-alvo]**, revise as opções do **[!UICONTROL Acionar]**, que permitem especificar a frequência de exibição da mensagem.

## Caso esteja usando um evento de inicialização como acionador:

O acionador só será ativado em uma nova sessão. Para obter mais informações sobre o início de uma sessão, consulte a linha `lifecycleTimeout` na [Configuração JSON](/help/android/configuration/json-config/json-config.md).

## Atualizei minha mensagem remotamente, mas meu aplicativo ainda exibe a mensagem antiga.

Lembre-se das seguintes informações:

* O gerenciamento dinâmico de tags pode levar alguns minutos para atualizar seu terminal com a nova definição. Aguarde um tempo e tente novamente.
* A configuração só será atualizada em um novo lançamento. Se o aplicativo tiver sido reiniciado dentro do tempo limite da sessão do ciclo de vida, é possível que a nova configuração não tenha sido baixada.

Para obter mais informações, consulte [Medições de ciclo de vida](/help/android/metrics.md).

## Minha imagem não se encaixa perfeitamente no espaço fornecido pelo modelo.

O modelo em tela cheia de mensagens no aplicativo é compatível com a exibição de uma imagem de um servidor remoto (URL da imagem) ou do conjunto de aplicativos (Imagem empacotada). A imagem deve estar em um formato padrão, por exemplo, JPG, GIF ou PNG. Como as telas dos dispositivos podem ter muitas dimensões diferentes, a imagem provavelmente não se encaixará perfeitamente no espaço fornecido pelo modelo. O modelo foca em mostrar o centro da imagem e, se ela não couber, recorta (retrato) ou esmaece (paisagem) as laterais.

Estas são as regras de posicionamento e dimensionamento para cada orientação:

* **Retrato**
   * Uma altura de 195 px para celulares.
   * Uma altura de 529 px para tablets.
   * Centralizado se a largura da imagem for menor que a largura do dispositivo.
   * Recortado se a largura da imagem for maior que a largura do dispositivo.

* **Paisagem**
   * A imagem foi dimensionada para 100% da altura do dispositivo.
   * A largura é de 75% do dispositivo, com um fade out à direita.

   Se tiver problemas com o modelo em tela cheia, você pode baixar e usar o modelo HTML personalizado. Este modelo oferece mais flexibilidade para imagens e permite o controle total do modelo.

