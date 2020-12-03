---
description: É possível definir o acionador de mensagem no aplicativo para ser a ID da mensagem de push que é enviada quando um usuário abre o aplicativo por meio da mensagem de push.
seo-description: É possível definir o acionador de mensagem no aplicativo para ser a ID da mensagem de push que é enviada quando um usuário abre o aplicativo por meio da mensagem de push.
seo-title: Acionar uma mensagem no aplicativo quando o aplicativo for aberto a partir de uma mensagem de push
title: Acionar uma mensagem no aplicativo quando o aplicativo for aberto a partir de uma mensagem de push
uuid: e1c8e29d-1c2b-47b2-8ab2-6b6e15df86f6
translation-type: tm+mt
source-git-commit: 114bce95e41c8e13695689dd2da2dbc04cb17ad7
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 59%

---


# Acionar uma mensagem no aplicativo quando o aplicativo for aberto a partir de uma mensagem por push{#trigger-an-in-app-message-when-the-app-is-opened-from-a-push-message}

É possível definir o acionador de mensagem no aplicativo para ser a ID da mensagem de push que é enviada quando um usuário abre o aplicativo por meio da mensagem de push.

1. Obtenha a ID da mensagem de push que será enviada para o usuário.

   Você pode encontrar a ID da mensagem de push no URL durante o fluxo de trabalho de criação da mensagem.

   Exemplo:

   ![](assets/brandon_task1.png)

1. Salve e ative a mensagem no aplicativo com o seguinte acionador:

   `“a.push.payloadID” =`

   >[!TIP]
   >
   >A ID da mensagem por push é a ID localizada na etapa 1.

   Este acionador deve ser adicionado manualmente pois não está disponível na lista suspensa **[!UICONTROL Acionador]**.

   ![](assets/brandon_task2.png)

1. Salve e envie a mensagem de push que contém a ID de push localizada na etapa 1.
1. Clique na mensagem de push para abrir o aplicativo e verificar se a mensagem no aplicativo é exibida ao abrir o aplicativo.

   Enquanto estiver testando, lembre-se das seguintes informações:

   * Depois de salvar a mensagem no aplicativo, demora cerca de 45 segundos para que o arquivo de configuração hospedado seja atualizado com a nova mensagem.
   * O aplicativo procura atualizações de arquivos de configuração (a nova mensagem no aplicativo) quando há uma **nova** inicialização, portanto, você deve garantir que o aplicativo esteja acionando uma nova inicialização quando a mensagem de push for clicada.

   Isso geralmente significa que é necessário garantir que o tempo limite da sessão tenha ocorrido. O tempo limite padrão é de 5 minutos.

