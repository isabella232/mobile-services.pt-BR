---
description: Estas informações ajudam a solucionar problemas de mensagem de push no aplicativo.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: Resolução de problemas nas mensagens no aplicativo
topic-fix: Metrics
uuid: 58533aa3-2eb2-4597-8525-77e4e5975e56
exl-id: ce009289-9d22-4d76-9997-31fc864e9d4d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 100%

---

# Resolução de problemas nas mensagens no aplicativo {#troubleshooting-in-app-messaging}

Estas informações ajudam a solucionar problemas de mensagem de push no aplicativo.

Se você concluiu todos os requisitos para mensagens no aplicativo, mas as mensagens não são exibidas, verifique os seguintes itens:

## Você está inserindo a nova configuração e o novo SDK no aplicativo?

Verifique se a versão do SDK é a 4.2 ou posterior e se está configurada corretamente. Certifique-se de que haja uma seção `Messages` em sua configuração (arquivo JSON baixado) ou um terminal remoto de mensagens para que ele possa ser recuperado do gerenciamento dinâmico de tags.

## Minha mensagem em tela cheia no Android não é exibida. Estou usando o SDK correto, a configuração e meus acionadores estão sendo atendidos.

Você atualizou o arquivo de manifesto para definir a atividade em tela cheia?

## Minha mensagem de notificação local no Android não está funcionando.

Certifique-se de que o destinatário de transmissão de notificação local esteja declarado no manifesto. Para obter mais informações, consulte a etapa 2 em [Habilitar mensagens no aplicativo](/help/android/messaging-main/messaging/messaging.md).

## A mensagem foi publicada?

Verifique a visualização da lista na página Gerenciar mensagens no aplicativo na coluna Status e verifique se ela está ativa.

## Observe as configurações *mostrar uma vez*, *mostrar sempre* e *mostrar offline* na guia Público-alvo.

Verifique se essas configurações estão definidas do modo como você deseja. Na guia **[!UICONTROL Público-alvo]**, revise as opções do **[!UICONTROL Acionar]**, que permitem especificar a frequência de exibição da mensagem.

## Caso esteja usando um evento de inicialização como acionador...

O acionador só será ativado em uma nova sessão. Para obter mais informações sobre o início de uma sessão, consulte a linha `lifecycleTimeout` no arquivo de Configuração JSON. Para obter mais informações, consulte [Configuração JSON do ADBMobile](/help/ios/configuration/json-config/json-config.md).

## Atualizei minha mensagem remotamente mas meu aplicativo ainda exibe a mensagem antiga.

Conclua uma das seguintes tarefas:

* O gerenciamento dinâmico de tags pode levar alguns minutos para atualizar seu terminal com a nova definição.

   Aguarde um tempo e tente novamente.

* A configuração só será atualizada em um novo lançamento.
Se o aplicativo tiver sido reiniciado dentro do tempo limite da sessão do ciclo de vida, é possível que a nova configuração não tenha sido baixada.

   Para obter mais informações, consulte [Medições de ciclo de vida](/help/ios/metrics.md).

## Minha imagem não se encaixa perfeitamente no espaço fornecido pelo modelo.

O modelo em tela cheia de mensagens no aplicativo é compatível com a exibição de uma imagem de um servidor remoto (URL da imagem) ou do conjunto de aplicativos (Imagem empacotada). A imagem deve estar em um formato padrão, por exemplo, JPG, GIF ou PNG.

Como as telas dos dispositivos podem ter muitas dimensões diferentes, a imagem provavelmente não se encaixará perfeitamente no espaço fornecido pelo modelo. O modelo foca em mostrar o centro da imagem e, se ela não couber, recorta (retrato) ou esmaece (paisagem) as laterais.

Estas são as regras de posicionamento e dimensionamento para cada orientação:

* **Retrato**:
   * Uma altura de 195 px para celulares
   * Uma altura de 529 px para tablets
   * Centralizado se a largura da imagem for menor que a largura do dispositivo.
   * Recortado se a largura da imagem for maior que a largura do dispositivo.

* **Paisagem**:
   * A imagem foi dimensionada para 100% da altura do dispositivo.
   * A largura é de 75% do dispositivo, com um fade out à direita.

Se tiver problemas com o modelo em tela cheia, você pode baixar e usar o modelo HTML personalizado. Este modelo oferece mais flexibilidade para imagens e permite o controle total do modelo.

## As mensagens no aplicativo em um iPhone X não são exibidas no modo de tela cheia.

Para exibir mensagens no aplicativo no modo de tela cheia em um iPhone X:

1. Adicione `viewport-fit=cover` na meta tag.

   ```html
   <meta name="viewport" content="viewport-fit=cover">
   ```

1. Configure o preenchimento apropriado no CSS para o elemento superior da interface do usuário, como:

   ```html
    topelement {
      padding-top:20px;
      /*Status bar height on iOS 11.0*/
      padding-top:constant(safe-area-inset-top);
      /*Status bar height on iOS 11+ */
      padding-top:env(safe-area-inset-top);
      } 
   ```

   Essas configurações impedem que os elementos da interface colidam com a barra de status.
