---
description: É possível definir o acionador de mensagem no aplicativo para ser a ID da mensagem de push que é enviada quando um usuário abre o aplicativo por meio da mensagem de push.
title: Acionar uma mensagem no aplicativo quando o aplicativo for aberto por uma mensagem de push
uuid: e1c8e29d-1c2b-47b2-8ab2-6b6e15df86f6
exl-id: 4496222f-b6f0-4fa1-86c6-149b590244d3
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 58%

---

# Acionar uma mensagem no aplicativo quando o aplicativo for aberto a partir de uma mensagem por push{#trigger-an-in-app-message-when-the-app-is-opened-from-a-push-message}

{#eol}

É possível definir o acionador de mensagem no aplicativo para ser a ID da mensagem de push que é enviada quando um usuário abre o aplicativo por meio da mensagem de push.

1. Obtenha a ID da mensagem de push que será enviada para o usuário.

   Você pode encontrar a ID da mensagem de push no URL durante o fluxo de trabalho de criação da mensagem.

   Exemplo:

   ![](assets/brandon_task1.png)

1. Salve e ative a mensagem no aplicativo com o seguinte acionador:

   `"a.push.payloadID" =`

   >[!TIP]
   >
   >A ID da mensagem por push é a ID localizada na etapa 1.

   Este acionador deve ser adicionado manualmente pois não está disponível na lista suspensa **[!UICONTROL Acionador]**.

   ![](assets/brandon_task2.png)

1. Salve e envie a mensagem de push que contém a ID de push localizada na etapa 1.
1. Clique na mensagem de push para abrir o aplicativo e verificar se a mensagem no aplicativo é exibida ao abrir o aplicativo.

   Durante o teste, lembre-se das seguintes informações:

   * Depois de salvar a mensagem no aplicativo, leva cerca de 45 segundos para que o arquivo de configuração hospedado seja atualizado com a nova mensagem.
   * O aplicativo busca atualizações do arquivo de configuração (a nova mensagem no aplicativo) quando há uma **novo** inicie, portanto, você deve garantir que o aplicativo esteja acionando uma nova inicialização ao clicar na mensagem de push.
   Isso geralmente significa que é necessário garantir que o tempo limite da sessão tenha ocorrido. O tempo limite padrão é de 5 minutos.
