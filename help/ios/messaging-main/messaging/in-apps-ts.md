---
description: Estas informações ajudam a solucionar problemas de mensagem de push no aplicativo.
keywords: mobile
seo-description: Estas informações ajudam a solucionar problemas de mensagem de push no aplicativo.
seo-title: Resolução de problemas nas mensagens no aplicativo
solution: Experience Cloud,Analytics
title: Resolução de problemas nas mensagens no aplicativo
topic: Métricas
uuid: 58533aa3-2eb2-4597-8525-77e4e5975e56
translation-type: ht
source-git-commit: 1154bab39b5215e00d47ad8e66caeec15e4e98de

---


# Resolução de problemas nas mensagens no aplicativo{#troubleshooting-in-app-messaging}

Estas informações ajudam a solucionar problemas de mensagem de push no aplicativo.

Se você concluiu todos os requisitos para as mensagens no aplicativo, mas as mensagens não são exibidas, verifique os seguintes itens:

## Você está inserindo a nova configuração e o novo SDK no aplicativo?

Verifique se a versão do SDK é 4.2 ou superior. Verifique também se ele foi configurado corretamente. Certifique-se de que haja uma seção `Messages` em sua configuração (arquivo JSON baixado) ou um terminal remoto de mensagens para que ele possa ser recuperado do gerenciamento dinâmico de tags.

## Minha mensagem de tela inteira não está aparecendo no Android. Estou usando o SDK correto e a configuração certa, mas meus acionadores não estão funcionando.

Você atualizou seu arquivo de manifesto para definir a atividade de tela inteira?

## Minha mensagem de notificação local no Android não está funcionando.

Certifique-se de que o destinatário de transmissão de notificação local esteja declarado no manifesto. Para obter mais informações, consulte a etapa 2 em [Habilitar mensagens no aplicativo](/help/android/messaging-main/messaging/messaging.md).

## A mensagem foi publicada?

Verifique a exibição de lista na página Gerenciar mensagens no aplicativo, localizada na coluna Status, e veja se ela foi publicada.

## Observe as configurações *mostrar uma vez*, *mostrar sempre* e *mostrar offline* na guia Público-alvo.

Verifique se essas configurações estão definidas do modo como você deseja. Na guia **[!UICONTROL Público-alvo]**, revise as opções do **[!UICONTROL Acionar]**, que permitem especificar a frequência de exibição da mensagem.

## Caso esteja usando um evento de inicialização como acionador...

O acionador só será ativado em uma nova sessão. Para obter mais informações sobre o início de uma sessão, consulte a linha `lifecycleTimeout` no arquivo de Configuração JSON. Para obter mais informações, consulte [Configuração JSON do ADBMobile](/help/ios/configuration/json-config/json-config.md).

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

1. Adicione `viewport-fit=cover` na meta tag.

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
