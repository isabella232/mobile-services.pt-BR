---
description: Perguntas frequentes sobre o Adobe Mobile Services e uma descrição geral dos recursos.
keywords: mobile
seo-description: Perguntas frequentes sobre o Adobe Mobile Services e uma descrição geral dos recursos.
seo-title: Perguntas frequentes
solution: Marketing Cloud, Analytics
title: Perguntas frequentes
topic: Métricas
uuid: 62 a 9241 c -2 ado -483 a-a 594-b 023916 cb 0 b 6
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Perguntas frequentes {#frequently-asked-questions}

A tabela a seguir contém uma lista de perguntas frequentes sobre o Adobe Mobile Services:

## SDK do Adobe Mobile {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### As atualizações no SDK são feitas com frequência?

Sim, fazemos alterações constantemente para fornecer os SDKs mais seguros, ricos em recursos e em conformidade com os padrões. Normalmente lançamos uma nova versão todos os meses. Essas atualizações do SDK são substituições diretas (para a versão 4x) para facilitar a implementação. Para obter mais informações sobre nossas atualizações, consulte nossas [Notas de versão](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html).

### Qual versão do SDK devo utilizar?

Nossos SDKs atuais estão na versão 4.11. Para obter mais informações, consulte nossas [Notas de versão](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html).

### Onde posso baixar os SDKs?

Os sdks para plataformas móveis individuais podem ser baixados ao visitar a seção [Gerenciar configurações](/help/using/c-manage-app-settings/c-manage-app-settings.md) do aplicativo.

### Como posso configurar os SDKs?

Depois de criar um novo conjunto de relatórios do aplicativo, navegue até Gerenciar configurações do aplicativo e configure todas as opções necessárias na página de informações do aplicativo. Depois de salvar a configuração, baixe os SDKs necessários na parte inferior da página Gerenciar configurações do aplicativo. The SDK will come pre-configured with the options you have saved and can be found in the `ADBMobileConfig.json` file in the SDK package. If you change any SDK settings on the Manage App Settings page, make sure you re-download the SDK files or update your `ADBMobileConfig.json` file with the necessary changes.

### Os SDKs do Adobe Mobile são compatíveis com IPv6 para iOS?

Os SDKs do Adobe Mobile usam pilhas de rede padrão do iOS e Android. Para iOS, o SDK usa nsurlsession (versões iOS 7 +) e nsurlconnection (versões iOS e posteriores do iOS), que são totalmente compatíveis com ipv 6. Os desenvolvedores que criaram ou usam sua própria pilha de rede podem querer revisar se houver outras considerações atenuantes. Estas são algumas informações adicionais da Apple:

*Se estiver escrevendo um aplicativo do cliente usando apis de rede de alto nível como os estruturas nsurlsession e cfnetwork e se conectar por nome, não será necessário alterar nada para que seu aplicativo funcione com endereços ipv 6.* Para obter mais informações, [consulte Suporte ao ipv 6 DNS 64/NAT 64 Networks](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1).


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### O que são Medições de ciclo de vida?

As Medições de ciclo de vida são métricas simples, coletadas automaticamente quando o SDK é implementado pela primeira vez no aplicativo. Para obter mais informações, consulte [Medições de ciclo de vida (Android)](/help/android/metrics.md) e [Medições de ciclo de vida (iOS)](/help/ios/metrics.md).

### Como posso solucionar problemas de regras de processamento?

Para obter mais informações, consulte [Dicas e truques para o processamento de regras](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html).

### Posso enviar os meus dados analíticos para vários conjuntos de relatórios?

Sim. Os SDKs oferecem a capacidade de enviar dados para vários conjuntos de relatórios do Adobe Analytics. Para capturar dados em vários conjunto de relatórios usando uma solicitação de imagem, defina as várias IDs de conjuntos de relatórios no campo **[!UICONTROL rsids]** na seção **analytics[!UICONTROL no arquivo , delimitadas por vírgulas e sem espaços.]**`ADBMobileConfig.json` Para obter mais informações, consulte [Configuração JSON do adbmobile](/help/ios/configuration/json-config/json-config.md).

### Como as visitas do Mobile são diferentes das inicializações?

Uma inicialização é medida pelo SDK quando um usuário abre o aplicativo pela primeira vez ou retorna a ele depois de permanecer fora dele por mais do que um valor de tempo limite especificado. The typical timeout is 5 minutes (300 seconds) in **[!UICONTROL lifecycleTimeout]** field, which is located in the `ADBMobileConfig.json` file. Uma visita é um cálculo do lado do servidor realizado pelo Adobe Analytics e se baseia na primeira e na última ocorrência de dados que são enviados pelo SDK, sem exceder o tempo limite de visita. Normalmente, o tempo limite de sessão é fixado em 30 minutos para um conjunto de relatórios. Embora as visitas provenham de análises da web tradicionais, essas ocorrências ainda fornecem informações valiosas sobre como os usuários entram e saem do seu aplicativo.

## Mensagens {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### Existem limitações de tamanho ou outras em relação às notificações de push?

As mensagens de notificação de push têm um limite de 140 caracteres. Não há limites de quantas notificações podem ser enviadas ou programadas ou quantas vezes elas são enviadas.

### É oferecido suporte para cargas personalizadas de notificações de push?

Sim, oferecemos suporte para uma carga de push personalizada que pode ser codificada no JSON. As cargas do Android e iOS são restritas à 4 KB e 2 KB respectivamente. Essas cargas são enviadas para o aplicativo por uma notificação de push ou local. Para obter mais informações, consulte [Experiência: Mensagem de push](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Existem limitações de tamanho nas mensagens do aplicativo?

As mensagens no aplicativo publicadas e ativas, criadas no Adobe Mobile Services, são hospedadas em um servidor com uma restrição de tamanho de 15 MB por conjunto de relatórios do aplicativo. Embora essa restrição se aplique ao conteúdo da mensagem e aos recursos hospedados na Adobe, não há restrições de quais recursos a mensagem no aplicativo pode referir-se em outros hosts ou aqueles dentro do aplicativo.

### Posso usar meu próprio HTML para mensagens no aplicativo?

Sim, oferecemos suporte de HTML personalizado para suas mensagens no aplicativo. For more information, see [Experience: In-App Message](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

### Quais acionadores posso usar para enviar notificações de push ou mensagens no aplicativo?

Os profissionais de marketing podem escolher todos os dados ou evento do Analytics enviados como um acionador para exibir as mensagens no aplicativo. As mensagens no aplicativo usam acionadores ativados localmente no dispositivo. Se vários acionadores forem escolhidos, todos devem ocorrer na mesma ocorrência para que a mensagem seja exibida. For more information, see [Experience: In-App Message](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

As mensagens de push são enviadas usando segmentos do Adobe Analytics pré-existentes ou segmentos personalizados que podem ser criados no dados de histórico do Analytics já coletados. Para obter mais informações, consulte [Experiência: Mensagem de push](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Por que recebo um erro com o nome do aplicativo, push ou link de marketing que digitei?

Você não pode usar a mesma mensagem no aplicativo e de push nem marcar o nome do link em vários aplicativos que usam o mesmo conjunto de relatórios principal ou VRS. Para resolver esse problema, insira outro nome para a mensagem no aplicativo, mensagem de push ou Link de marketing.

## Localização {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### Há um limite de quantas oints de interesse (POIs) posso ter?

Não há restrição específica, mas para um desempenho ideal e devido a restrições de memória no dispositivo do usuário, recomendamos criar ou carregar no máximo 5000 POIs.

## Aquisição {#section_B37F1129CD5843E890D0E54179455357}

### Posso atribuir campanhas para atividades no aplicativo?

Sim. O Adobe Mobile Services pode auxiliar na criação de truques de marketing que ajudam a promover e direcionar o tráfego para seus aplicativos e vincular campanhas de aquisição para análise e conversões no aplicativo. Para obter mais informações, consulte [Aquisição](/help/using/acquisition-main/acquisition-main.md).

### Como posso configurar links para adquirir e rastrear novos usuários do aplicativo?

Você pode criar Links de publicidade que encaminham os usuários para baixar aplicativos na Apple App Store e no Google Play. Esses links permitem atribuir seus eventos de sucesso aos downloads. Para obter mais informações, consulte [Criador de links de marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).