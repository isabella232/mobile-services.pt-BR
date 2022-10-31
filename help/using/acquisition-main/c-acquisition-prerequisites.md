---
description: Conclua os seguintes pré-requisitos para usar os links de aquisição.
keywords: dispositivos móveis
solution: Experience Cloud Services,Analytics
title: Pré-requisitos de aquisição
topic-fix: Metrics
uuid: a224499a-5a51-4ca5-a37b-06792b774671
exl-id: 31201bec-e823-47b1-8912-2f8d69cea5be
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 100%

---

# Pré-requisitos de aquisição {#acquisition-prerequisites}

{#eol}

Observe os seguintes pré-requisitos para usar os links de aquisição.

Para rastrear os Links de marketing, deve-se atender aos seguintes pré-requisitos:

1. Verifique se você tem um conjunto de relatórios do aplicativo móvel.

   Você deve criar um novo conjunto de relatórios do aplicativo móvel ou ter um conjunto de relatórios existente que possa coletar, rastrear e gerar relatórios sobre os dados coletados dos Links de marketing. Para obter mais informações sobre como criar um novo conjunto de relatórios de aplicativo móvel, consulte [Adicionar um novo aplicativo](/help/using/manage-apps/t-new-app.md).

1. Verifique a versão do SDK.

   A funcionalidade de rastreamento de Links de marketing mais recente exige o SDK versão 4.9 ou posterior.

   **Funcionalidade suportada**

   | Versão do SDK | [Construtor de aquisição herdada](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md) | [Criação manual de links](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md) | [Construtor de links de publicidade](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md) |
   |--- |--- |--- |--- |
   | 4.1 a 4.5 | Sim | Não | Não |
   | 4.6 a 4.9 | Sim | Sim | Não |
   | 4.9 ou posterior | Sim | Sim | Sim |

1. Habilitar as opções de Aquisição do SDK

   O rastreamento deve ser ativado na configuração do SDK para que os links possam ser rastreados e relatados. Para obter mais informações, consulte [Configurar aquisição](/help/using/acquisition-main/t-enable-acquisition.md).

1. Adicionar aplicativos da loja de aplicativos

   Você deve adicionar um aplicativo da Apple App Store ou do Google Play. Para obter mais informações, consulte [Adicionar um aplicativo de uma loja de aplicativos](/help/using/manage-apps/c-app-store/t-app-store-app.md).
