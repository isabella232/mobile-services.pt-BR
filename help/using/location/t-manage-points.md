---
description: É possível criar e gerenciar pontos de interesse, que permitem definir localizações geográficas que você pode usar para fins de correlação, para segmentar com mensagens no aplicativo e muito mais. Quando uma ocorrência é enviada em um ponto de interesse, ele é anexado à ocorrência.
keywords: mobile
seo-description: É possível criar e gerenciar pontos de interesse, que permitem definir localizações geográficas que você pode usar para fins de correlação, para segmentar com mensagens no aplicativo e muito mais. Quando uma ocorrência é enviada em um ponto de interesse, ele é anexado à ocorrência.
seo-title: Gerenciar pontos de interesse
solution: Marketing Cloud,Analytics
title: Gerenciar pontos de interesse
topic: Métricas
uuid: 7b362534-54fb-43a3-b6b2-dfc8f45ff7c6
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Manage points of interest {#manage-points-of-interest}

Você pode criar e gerenciar POIs, que permitem definir localizações geográficas que podem ser usadas para fins de correlação, direcionamento para mensagens no aplicativo e assim por diante. Quando uma ocorrência é enviada em um POI, o POI é anexado à ocorrência.

Antes de usar o Local, verifique os seguintes requisitos:

* Você deve ter o Analytics—Mobile Apps ou o Analytics Premium.
* Você deve ativar **[!UICONTROL Relatórios de localização]no aplicativo.**
* If you are using a version of the iOS SDK or Android SDK older than version 4.2, after adding new **[!UICONTROL Points of Interest]**, you must download a new configuration file and give it to your app developers.

   If you are using the iOS SDK or Android SDK version 4.2 or later, you do not need to submit an app update to the store to update your **[!UICONTROL Points of Interest]**. Na página Gerenciar pontos de interesse, ao clicar em **[!UICONTROL Salvar]**, as alterações são empacotadas para a lista **[!UICONTROL Pontos de interesse]** e o arquivo de configuração do aplicativo ativo é atualizado. Saving also updates the list of points in your app on the user devices, as long as the app uses the updated SDK and configuration with a remote POI URL.

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

      Digite o raio (em metros) ao redor do **[!UICONTROL Ponto de localização]que você deseja incluir.** Por exemplo, se você criar um POI para Denver, Colorado, poderá especificar um raio grande o suficiente para incluir a cidade de Denver e as áreas adjacentes, mas excluir Colorado Springs.

   * **[!UICONTROL Ícone do mapa]**

      Select an icon that will display on the Overview and Map reports.[](/help/using/location/c-location-overview.md)[](/help/using/location/c-map-points.md)

1. Adicione POIs adicionais, conforme necessário.

   Recomendamos que você adicione no máximo 5.000 POIs. Se você adicionar mais de cinco mil, poderá salvá-los, mas receberá uma mensagem de aviso informando que as práticas recomendadas exigem menos de cinco mil pontos.

1. Clique em **[!UICONTROL Salvar]**.

To delete one or more POIs, select the applicable check boxes, and click **[!UICONTROL Remove Selected]**.

Click **[!UICONTROL Import]** or **[!UICONTROL Export]** to work with the data by using a `.csv` file instead of using the Adobe Mobile user interface.
