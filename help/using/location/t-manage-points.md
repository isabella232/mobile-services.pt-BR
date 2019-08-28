---
description: É possível criar e gerenciar pontos de interesse, que permitem definir localizações geográficas que você pode usar para fins de correlação, para segmentar com mensagens no aplicativo e muito mais. Quando uma ocorrência é enviada em um ponto de interesse, ele é anexado à ocorrência.
keywords: mobile
seo-description: É possível criar e gerenciar pontos de interesse, que permitem definir localizações geográficas que você pode usar para fins de correlação, para segmentar com mensagens no aplicativo e muito mais. Quando uma ocorrência é enviada em um ponto de interesse, ele é anexado à ocorrência.
seo-title: Gerenciar pontos de interesse
solution: Marketing Cloud, Analytics
title: Gerenciar pontos de interesse
topic: Métricas
uuid: 7 b 362534-54 fb -43 a 3-b 6 b 2-dfc 8 f 45 ff 7 c 6
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Manage points of interest {#manage-points-of-interest}

É possível criar e gerenciar POIs, o que permite definir localizações geográficas que você pode usar para fins de correlação, direcionamento com mensagens no aplicativo e assim por diante. Quando uma ocorrência é enviada em um POI, o POI é anexado à ocorrência.

Antes de poder usar o Local, verifique os seguintes requisitos:

* Você deve ter o Analytics—Mobile Apps ou o Analytics Premium.
* Você deve ativar **[!UICONTROL Relatórios de localização]no aplicativo.**
* If you are using a version of the iOS SDK or Android SDK older than version 4.2, after adding new **[!UICONTROL Points of Interest]**, you must download a new configuration file and give it to your app developers.

   If you are using the iOS SDK or Android SDK version 4.2 or later, you do not need to submit an app update to the store to update your **[!UICONTROL Points of Interest]**. Na página Gerenciar pontos de interesse, quando você clica **[!UICONTROL em Salvar]**, as alterações são empacotadas para a lista **[!UICONTROL de Pontos de interesse]** e o arquivo de configuração do aplicativo ativo é atualizado. Salvar também atualiza a lista de pontos no aplicativo nos dispositivos do usuário, desde que o aplicativo utilize o SDK e a configuração atualizados com um URL de POI remoto.

On the user's device, for a hit to be assigned to a **[!UICONTROL Points of Interest]**, location must be enabled for the app.

Para usar o Local, conclua as seguintes tarefas:

1. Clique no nome do aplicativo para ir para a página Gerenciar configurações do aplicativo.
1. Click **[!UICONTROL Location]** &gt; **[!UICONTROL Manage Points of Interest]**.

   ![Resultado da etapa](assets/poi.png)

1. Digite as informações em cada um dos seguintes campos:

   * **[!UICONTROL Nome do ponto]**

      Digite o nome do **[!UICONTROL Ponto de localização.]**

      Pode ser o nome de uma cidade, de um país, de uma região. Você também pode criar um **[!UICONTROL Ponto de Localização]em locais específicos, como estádios ou empresas.**

   * **[!UICONTROL Latitude]**

      Especifique a latitude do **[!UICONTROL Ponto de localização]**. Você pode encontrar essas informações em outras fontes, inclusive na Internet.

   * **[!UICONTROL Longitude]**

      Especifique a longitude do **[!UICONTROL Ponto de localização]**. Você pode encontrar essas informações em outras fontes, inclusive na Internet.

   * **[!UICONTROL Raio (metros)]**

      Digite o raio (em metros) ao redor do **[!UICONTROL Ponto de localização]que você deseja incluir.** Por exemplo, se você criar um POI para Denver, Colorado, poderá especificar um raio com tamanho suficiente para incluir a cidade de Denver e as áreas subjacentes, mas excluir Colorado Springs.

   * **[!UICONTROL Ícone do mapa]**

      Selecione um ícone que será exibido nos relatórios [Visão geral](/help/using/location/c-location-overview.md) e [Mapa](/help/using/location/c-map-points.md) .

1. Adicione POIs, conforme necessário.

   Recomendamos que você adicione mais de 5,000 POIs. Se você adicionar mais de cinco mil, poderá salvá-los, mas receberá uma mensagem de aviso informando que as práticas recomendadas exigem menos de cinco mil pontos.

1. Clique em **[!UICONTROL Salvar]**.

To delete one or more POIs, select the applicable check boxes, and click **[!UICONTROL Remove Selected]**.

Click **[!UICONTROL Import]** or **[!UICONTROL Export]** to work with the data by using a `.csv` file instead of using the Adobe Mobile user interface.
