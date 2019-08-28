---
description: Estas informações ajudam a solucionar problemas de mensagem de push no aplicativo.
keywords: mobile
seo-description: Estas informações ajudam a solucionar problemas de mensagem de push no aplicativo.
seo-title: Resolução de problemas nas mensagens no aplicativo
solution: Marketing Cloud, Analytics
title: Resolução de problemas nas mensagens no aplicativo
topic: Métricas
uuid: 58533 aa 3-2 eb 2-4597-8525-77 e 4 e 5975 e 56
translation-type: tm+mt
source-git-commit: 1154bab39b5215e00d47ad8e66caeec15e4e98de

---


# Troubleshooting in-app messaging{#troubleshooting-in-app-messaging}

Estas informações ajudam a solucionar problemas de mensagem de push no aplicativo.

Se você concluiu todos os requisitos para as mensagens no aplicativo, mas as mensagens não são exibidas, verifique os seguintes itens:

## Você está inserindo a nova configuração e o novo SDK no aplicativo?

Verifique se a versão do SDK é 4.2 ou superior. Verifique também se ele foi configurado corretamente. Ensure that you have a `Messages` section in your configuration (downloaded JSON file), or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## Minha mensagem de tela inteira não está aparecendo no Android. Estou usando o SDK correto e a configuração certa, mas meus acionadores não estão funcionando.

Você atualizou seu arquivo de manifesto para definir a atividade de tela inteira?

## Minha mensagem de notificação local no Android não está funcionando.

Certifique-se de que o destinatário de transmissão de notificação local esteja declarado no manifesto. For more information, see step 2 in [Enabling In-App Messages](/help/android/messaging-main/messaging/messaging.md).

## A mensagem foi publicada?

Verifique a exibição de lista na página Gerenciar mensagens no aplicativo, localizada na coluna Status, e veja se ela foi publicada.

## Observe *mostrar uma vez*, *mostrar sempre*, *mostrar* configurações offline na guia Público-alvo.

Verifique se essas configurações estão definidas do modo como você deseja. Na guia **[!UICONTROL Público-alvo]**, revise as opções do **Acionar], que permitem especificar a frequência de exibição da mensagem.[!UICONTROL **

## Caso esteja usando um evento de inicialização como acionador...

O acionador só será ativado em uma nova sessão. For more information about when a session begins, see the `lifecycleTimeout` row in the JSON Config file. Para obter mais informações, consulte [Configuração JSON do adbmobile](/help/ios/configuration/json-config/json-config.md).

## Atualizei minha mensagem remotamente, mas meu aplicativo ainda exibe a mensagem antiga.

Conclua uma das seguintes tarefas:

* O gerenciamento dinâmico de tags pode levar alguns minutos para atualizar seu terminal com a nova definição.

   Aguarde um tempo e tente novamente.

* A configuração só será atualizada em um novo lançamento.
Se o aplicativo tiver sido reiniciado dentro do tempo limite da sessão do ciclo de vida, é possível que a nova configuração não tenha sido baixada.

   Para obter mais informações, consulte [Medições de ciclo de vida](/help/ios/metrics.md).

## Minha imagem não se encaixa perfeitamente no espaço fornecido pelo modelo.

O modelo em tela cheia das mensagens no aplicativo é compatível com a exibição de imagens de um servidor remoto (URL da imagem) ou do conjunto de aplicativos (Imagem embutida). A imagem deve estar em um formato padrão, por exemplo, JPG, GIF ou PNG.

Como as telas dos dispositivos podem ter muitas dimensões diferentes, a imagem provavelmente não se encaixará perfeitamente no espaço fornecido pelo modelo. O modelo foca em mostrar o centro da imagem e, se ela não couber, recorta (retrato) ou esmaece (paisagem) as laterais.

Estas são as regras de posicionamento e dimensionamento para cada orientação:

* **Retrato**:
   * Uma altura de 195 px para celulares
   * Uma altura de 529 px para tablets
   * Centralizado se a largura da imagem for menor que a largura do dispositivo.
   * Recortado se a largura da imagem for maior que a largura do dispositivo.

* **Paisagem**:
   * A imagem é dimensionada para 100% da altura do dispositivo.
   * A largura é 75% do dispositivo e esmaecida à direita.

Se tiver problemas com o modelo em tela cheia, é possível baixar e usar o modelo de HTML personalizado. O modelo HTML personalizado proporciona maior flexibilidade para imagens e permite controlar totalmente o modelo.

## Mensagens no aplicativo em um iPhone X não são exibidas no modo de tela cheia.

Para exibir mensagens no aplicativo no modo de tela cheia em um iPhone X:

1. Add `viewport-fit=cover` in the meta tag.

   ```html
   <meta name="viewport" content="viewport-fit=cover">
   ```

1. Configure o preenchimento adequado no CSS para o elemento principal de interface do usuário, como:

   ```html
   topelement {
     padding-top:20px;
     /*Status bar height on iOS 11.0*/
     padding-top:constant(safe-area-inset-top);
     /*Status bar height on iOS 11+ */
     padding-top:env(safe-area-inset-top);
     } 
   ```

   Essas configurações impedem a colisão de elementos da interface do usuário com a barra de status.
