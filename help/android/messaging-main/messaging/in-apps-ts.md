---
description: Estas informações ajudam a solucionar problemas de mensagem de push no aplicativo.
keywords: mobile
seo-description: Estas informações ajudam a solucionar problemas de mensagem de push no aplicativo.
seo-title: Solução de problemas de mensagens no aplicativo
solution: Marketing Cloud, Analytics
title: Solução de problemas de mensagens no aplicativo
topic: Métricas
uuid: 39 c 3 a 21 d -92 c 2-4004-b 00 f -99 b 6 f 91 d 3696
translation-type: tm+mt
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# Solução de problemas de mensagens no aplicativo{#troubleshooting-in-app-messaging}

Estas informações ajudam a solucionar problemas de mensagem de push no aplicativo.

Se você concluiu todos os requisitos para as mensagens no aplicativo, mas as mensagens não são exibidas, verifique os seguintes itens:

## Você está inserindo a nova configuração e o novo SDK no aplicativo?

Ensure that you have an [In-App Messaging](/help/android/messaging-main/messaging/messaging.md) section in your configuration (downloaded JSON file) or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## Minha mensagem de tela inteira não está aparecendo no Android. Estou usando o SDK correto e a configuração certa, mas meus acionadores não estão funcionando.

Você atualizou seu arquivo de manifesto para definir a atividade de tela inteira?

## Minha mensagem de notificação local no Android não está funcionando.

Certifique-se de que o destinatário de transmissão de notificação local esteja declarado no manifesto. For more information, see step 2 in *Enabling In-App Messaging* in [In-App Messaging](/help/android/messaging-main/messaging/messaging.md).

## A mensagem foi publicada?

Para verificar se a mensagem é em tempo real, na página Gerenciar mensagens no aplicativo, na coluna **Status**, verifique a lista de mensagens.

## Observe *mostrar uma vez*, *mostrar sempre*, *mostrar* configurações offline na guia Público-alvo.

Verifique se essas configurações estão definidas do modo como você deseja. Na guia **[!UICONTROL Público-alvo]**, revise as opções do **Acionar], que permitem especificar a frequência de exibição da mensagem.[!UICONTROL **

## Se estiver usando um evento de inicialização como acionador…

O acionador só será ativado em uma nova sessão. Para obter mais informações sobre o início de uma sessão, consulte a linha `lifecycleTimeout` na [Configuração JSON](/help/android/configuration/json-config/json-config.md).

## Atualizei minha mensagem remotamente, mas meu aplicativo ainda exibe a mensagem antiga.

Lembre-se das seguintes informações:

* O gerenciamento dinâmico de tags pode levar alguns minutos para atualizar seu terminal com a nova definição. Aguarde um tempo e tente novamente.
* A configuração só será atualizada em um novo lançamento. Se o aplicativo tiver sido reiniciado dentro do tempo limite da sessão do ciclo de vida, é possível que a nova configuração não tenha sido baixada.

Para obter mais informações, consulte [Medições de ciclo de vida](/help/android/metrics.md).

## Minha imagem não se encaixa perfeitamente no espaço fornecido pelo modelo.

O modelo em tela cheia das mensagens no aplicativo é compatível com a exibição de imagens de um servidor remoto (URL da imagem) ou do conjunto de aplicativos (Imagem embutida). A imagem deve estar em um formato padrão, por exemplo, JPG, GIF ou PNG. Como as telas dos dispositivos podem ter muitas dimensões diferentes, a imagem provavelmente não se encaixará perfeitamente no espaço fornecido pelo modelo. O modelo foca em mostrar o centro da imagem e, se ela não couber, recorta (retrato) ou esmaece (paisagem) as laterais.

Estas são as regras de posicionamento e dimensionamento para cada orientação:

* **Retrato**
   * Uma altura de 195 px para celulares.
   * Uma altura de 529 px para tablets.
   * Centralizado se a largura da imagem for menor que a largura do dispositivo.
   * Recortado se a largura da imagem for maior que a largura do dispositivo.

* **Paisagem**
   * A imagem é dimensionada para 100% da altura do dispositivo.
   * A largura é 75% do dispositivo e esmaecida à direita.
   Se tiver problemas com o modelo em tela cheia, é possível baixar e usar o modelo de HTML personalizado. O modelo HTML personalizado proporciona maior flexibilidade para imagens e permite controlar totalmente o modelo.

