---
description: Você pode acompanhar e gerenciar os dados recebidos do aplicativo ao configurar diversas variáveis e métricas.
keywords: mobile
seo-description: Você pode acompanhar e gerenciar os dados recebidos do aplicativo ao configurar diversas variáveis e métricas.
seo-title: Gerenciamento do aplicativo
solution: Marketing Cloud, Analytics
title: Gerenciamento do aplicativo
topic: Métricas
uuid: 0 cc 356 c 3-8457-40 a 7-8 c 97-7 cbc 68 a 5 dc 0 c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Gerenciamento do aplicativo {#managing-your-app}

Você pode acompanhar e gerenciar os dados recebidos do aplicativo ao configurar diversas variáveis e métricas.

## Gerenciar variáveis e métricas {#section_EC2D58AC334F4ED49E764B81C2423A62}

* **Variáveis e métricas padrão**

   Cada aplicativo inclui variáveis e métricas para acompanhar atividades de compras e do carrinho de compras. Some purchase information cannot be handled with processing rules, so the SDK exposes the special `"&&products"` context data. Por exemplo, você pode ter variáveis como adições de carrinho, remoções de carrinho, finalizações, pedidos etc. Os dados de contexto devem ser mapeados para dados no Adobe Analytics. Se essa variável for preenchida como um mapeamento simples dos dados de contexto, essa é a chave que realiza o mapeamento. Deixe em branco se a variável estiver preenchida por regras mais complexas nas Ferramentas administrativas do Analytics.

   Para obter mais informações sobre essas variáveis e métricas, consulte o seguinte:

   * [Variáveis de produto no Android](/help/android/analytics-main/products/products.md)
   * [Variáveis de produto no iOS](/help/ios/analytics-main/products/products.md)

* **Variáveis personalizadas**

   A página Variáveis personalizadas exibe todas as variáveis personalizadas do Analytics que são configuradas para o conjunto de relatórios com os dados do aplicativo. Nessa página, você pode habilitar mais variáveis e mapear dados de contexto diretamente nas variáveis do Analytics.

### Mapeamento de dados de contexto a variáveis do Analytics

Click **[!UICONTROL Manage App Settings]** &gt; **[!UICONTROL Manage Variables &amp; Metrics]** &gt; **[!UICONTROL Custom Variables]**.

These mappings call the same API that is used in [Processing Rules](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

![Mapeamento de dados de contexto](assets/custom_data_content.png)

Esta é uma lista das variáveis personalizadas que você pode configurar:

* The **[!UICONTROL Custom Properties]** (or props) answer the question "which one?" As props podem ser definidas com um valor de texto que será associado a outras variáveis e métricas enviadas na mesma ocorrência. Os valores podem ser usados para filtrar relatórios ou podem ser classificados de acordo com uma métrica associada.

   Quando um valor está definido para uma propriedade em uma chamada de rastreamento (ou ocorrência), ele se aplica somente a essa chamada.

* The **[!UICONTROL Custom Variables]** (or evars) also answer the question "which one?" Entretanto, um valor de eVar pode aplicar-se não apenas a uma ocorrência para a qual foi enviado, mas também às variáveis e métricas enviadas em ocorrências subsequentes até o valor expirar ou um novo ser definido.
* The **[!UICONTROL Custom List Variables (or Multi-Value Variables)]** behave the same as variables except they allow you to capture multiple values on one hit. Para obter mais informações, consulte [Variáveis de lista](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/variables-analytics-reporting/page-variables.html).

Os seguintes mapeamentos são exibidos no Analytics como sendo criados no Mobile Services.

* **[!UICONTROL Nome]**

   O nome amigável para a variável de coleção de dados.

* **[!UICONTROL Dados de contexto]**

   Se essa variável for preenchida como um mapeamento simples dos dados de contexto, essa é a chave que realiza o mapeamento. Deixe esse campo em branco caso a variável esteja preenchida por regras mais complexas nas Ferramentas de administrador do Analytics.

   Clique na coluna de dados de contexto e selecione a variável de dados de contexto que deseja mapear. A lista suspensa contém as variáveis recebidas nos últimos 30 dias. Dessa forma, caso os dados de contexto que você deseja mapear não estejam na lista, basta digitá-los.

* **[!UICONTROL Persistência (Variáveis personalizadas e Variáveis personalizadas de lista)]**

   A persistência determina o ponto em que o valor de uma Variável personalizada (eVar) expirará ou não será mais associado a ocorrências adicionais. Se uma eVar tiver expirado ao disparar uma ocorrência, o valor Nenhum será associado à ocorrência para essa eVar. Isso significa que nenhum valor de eVar estava ativo quando a ocorrência foi disparada.

   Você pode selecionar uma das seguintes opções:

   * **[!UICONTROL Sessão]**

      O valor da evar persiste durante a visita do Analytics.

   * **[!UICONTROL Chamada de rastreamento]**

      O valor da evar persiste somente para a chamada de rastreamento ou ocorrência na qual foi incluído.

   * **[!UICONTROL Nunca expira]**

      O valor da evar persiste para todas as chamadas de rastreamento subsequentes.
   * **[!UICONTROL Avançado]**

      O Adobe Analytics possui uma interface do usuário mais avançada para configurar a persistência de eVars. Se um valor de persistência for definido para a evar que não é compatível com o Mobile Services, esse valor será exibido na interface do usuário do Mobile Services.

      To manage eVars, click **[!UICONTROL Adobe Analytics Report Suite Manager]** &gt; **[!UICONTROL Conversion Variables UI]**.

   * **[!UICONTROL Suporte de listas]**

      Permite que vários valores sejam associados com a propriedade em uma chamada de rastreamento. O delimitador deve ter um caractere e não pode ser zero ou um espaço.

   * **[!UICONTROL Delimitador]**

      O delimitador deve ter um caractere e não pode ser zero ou um espaço.

### Variáveis adicionais do Analytics

Você pode ativar variáveis adicionais usando a lista suspensa na parte inferior de cada seção de variável.

![adicionar uma variável](assets/add_variable.png)

Selecione um número de variável não utilizado e digite um nome. Opcionalmente, você pode fornecer a variável de dados de contexto que gostaria de armazenar e qualquer informação adicional.

* **Métricas personalizadas**

   Métricas (ou eventos) respondem às perguntas *quanto?* ou *quantos?*. Os eventos podem aumentar sempre que o usuário tomar uma ação ou manter valores numéricos, como um preço. As métricas personalizadas incluem eventos como a criação de um aplicativo, o download ou a exportação de um arquivo PDF ou CSV, o salvamento de uma campanha, o download do SDK, a execução de um relatório, a adição de um link à App Store, a ativação de uma mensagem no aplicativo e assim por diante.

   Selecione um dos seguintes tipos de métricas personalizadas:

   * **[!UICONTROL Número inteiro]**
   * **[!UICONTROL Número decimal]**
   * **[!UICONTROL Moeda]**

## Gerenciar pontos de interesse {#section_990EF15E4E3B42CC807FCD9BEC8DB4C6}

Pontos de interesse permitem definir locais geográficos que podem ser usados para fins de correlação, direcionamento com mensagens no aplicativo e assim por diante. Quando uma ocorrência é enviada em um ponto de interesse, ele é anexado à ocorrência. Para obter mais informações sobre pontos de interesse, consulte [Gerenciar pontos de interesse](/help/using/location/t-manage-points.md).

## Gerenciar destinos do link {#section_F722A387E22A430187B063D358A87711}

Você pode criar, editar, arquivar/desarquivar e excluir destinos de links. Esses destinos podem ser chamados em linha ao criar Links de publicidade, notificações por push ou mensagens no aplicativo. Para obter mais informações sobre destinos de links, consulte [Gerenciar destinos de links](/help/using/acquisition-main/c-manage-link-destinations/t-archive-unarchive-link-destinations.md).

## Gerenciar postbacks {#section_78B0A8D7AE6940E78D85AE3AB829E860}

Os postbacks permitem enviar os dados coletados pelo Adobe Mobile a um servidor separado de terceiros. Ao usar os mesmos acionadores e características usados para exibir uma mensagem no aplicativo, é possível configurar o Mobile para enviar dados personalizados a um destino de terceiros. Para obter mais informações sobre postbacks, consulte [Configuração de postbacks](/help/using/c-manage-app-settings/c-mob-confg-app/signals.md).
