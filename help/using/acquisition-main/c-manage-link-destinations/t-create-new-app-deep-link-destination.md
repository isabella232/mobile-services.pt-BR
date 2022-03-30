---
description: É possível criar um novo destino de link que direciona os usuários para a Web ou um deep link no seu aplicativo.
keywords: dispositivos móveis
solution: Experience Cloud Services,Analytics
title: Criar novo destino de link
topic-fix: Metrics
uuid: 390e3dea-0221-4f97-980d-a90ca9f162fa
exl-id: 2d2f5938-1461-43e2-a375-45c18afc9d5a
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 100%

---

# Criar um novo destino de link {#create-new-link-destination}

É possível criar um novo destino de link que direciona os usuários para a Web ou um deep link no seu aplicativo.

1. Na interface do Mobile Services, clique em **[!UICONTROL Gerenciar aplicativos]**.
1. Clique no nome do aplicativo para exibir a página Informações do aplicativo.
1. Clique em **[!UICONTROL Gerenciar destinos do link]**.
1. Clique em **[!UICONTROL Criar novo]**.
1. Digite informações nos seguintes campos:
   * **[!UICONTROL Title]**

      Digite um nome descritivo para o destino do link do aplicativo. O título é exibido apenas na página Gerenciar destinos de links na interface do usuário do Adobe Mobile Services. Um nome descritivo ajuda você ou outras pessoas na sua organização a encontrar rapidamente um destino do link específico e pode fornecer informações sobre a sua finalidade.

   * **[!UICONTROL Tipo de link]**

      Veja a seguir uma lista dos tipos de links disponíveis:

      * **[!UICONTROL Deep link do aplicativo]**

         Forneça um link profundo de esquema URI (por exemplo, `yourapp://section`). Os destinos de deep link de aplicativo são deep link de esquema de URI que direcionam os usuários para um deep link no seu aplicativo. Por exemplo, você pode direcionar os usuários para uma linha de produtos específica no aplicativo móvel de um varejista online.

      * **[!UICONTROL Link da Web]**

         Digite um URL HTTP ou HTTPS, por exemplo, `https://adobe.com`. Os destinos de links da Web direcionam os usuários para um URL. Por exemplo, você pode direcionar os usuários para uma linha de produtos no site de um varejista online.

      * **[!UICONTROL Link híbrido]**

         Digite um Link universal do iOS ou um Link do aplicativo Android (por exemplo, `https://yourwebsite.com`). Os links híbridos são compatíveis com os Links universais do iOS e os Links de aplicativo do Android.
   * **[!UICONTROL Aplicativo]**
Selecione o aplicativo que está associado ao link que você vai fornecer.

      >[!TIP]
      >
      >Essas informações serão necessárias somente se você tiver selecionado um link profundo do aplicativo ou um link híbrido no **[!UICONTROL Tipo de link]**. Se o aplicativo não for exibido na lista de seleção, clique em **[!UICONTROL Adicionar novo aplicativo]** para fazer referência a um novo aplicativo em uma app store.

   * **[!UICONTROL Tipo de link]**

      Digite o URL real do link selecionado. O rótulo deste campo varia dependendo do tipo de link selecionado.

   * **[!UICONTROL Notas]**

      Digite as notas opcionais para o seu destino. As notas adicionais são exibidas somente na página Gerenciar destinos de links na interface do usuário do Adobe Mobile Services. As notas adicionais podem ajudar você ou outras pessoas na sua organização a encontrar rapidamente um destino de link específico e podem fornecer informações sobre a sua finalidade, a campanha associada ou qualquer outra coisa considerada importante.


1. Clique em **Salvar**.
