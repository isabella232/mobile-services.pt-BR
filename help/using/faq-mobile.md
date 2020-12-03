---
description: Perguntas frequentes sobre o Adobe Mobile Services e uma descrição geral dos recursos.
keywords: mobile
seo-description: Perguntas frequentes sobre o Adobe Mobile Services e uma descrição geral dos recursos.
seo-title: Perguntas frequentes
solution: Experience Cloud,Analytics
title: Perguntas frequentes
topic: Metrics
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 100%

---


# Perguntas frequentes {#frequently-asked-questions}

A tabela a seguir contém uma lista de perguntas frequentes sobre o Adobe Mobile Services:

## SDK do Adobe Mobile {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### O SDK é atualizado com frequência?

Sim, estamos constantemente fazendo atualizações para obter os SDKs mais ricos em recursos, compatíveis com padrões e seguros. Normalmente lançamos uma nova versão todos os meses. Essas atualizações do SDK são substituições diretas (para a versão 4x) para facilitar a implementação. Para obter mais informações sobre nossas atualizações, consulte as [Notas de versão](https://docs.adobe.com/content/help/pt-BR/release-notes/experience-cloud/current.html).

### Qual versão do SDK devo utilizar?

Nossos SDKs atuais estão na versão 4.11. Para obter mais informações, consulte as [Notas de versão](https://docs.adobe.com/content/help/pt-BR/release-notes/experience-cloud/current.html).

### Onde posso baixar os SDKs?

Os SDKs para plataformas móveis individuais podem ser baixados na seção [Gerenciar configurações do aplicativo](/help/using/c-manage-app-settings/c-manage-app-settings.md).

### Como posso configurar os SDKs?

Depois de criar um novo conjunto de relatórios de aplicativos, vá para Gerenciar configurações do aplicativo e configure todas as opções necessárias na página de informações do aplicativo. Depois de salvar a configuração, baixe os SDKs necessários na parte inferior da página Gerenciar configurações do aplicativo. O SDK virá pré-configurado com as opções salvas e pode ser encontrado no arquivo `ADBMobileConfig.json` dentro do pacote SDK. Se você alterar as configurações do SDK na página Gerenciar configurações do aplicativo, baixe novamente os arquivos do SDK ou atualize seu arquivo `ADBMobileConfig.json` com as alterações necessárias.

### Os SDKs do Adobe Mobile são compatíveis com IPv6 para iOS?

Os SDKs do Adobe Mobile usam as pilhas de rede padrão do iOS e do Android. Para iOS, o SDK usa NSURLSession (versões do iOS 7 ou posteriores) e NSURLConnection (versões do iOS 7 ou posteriores), que são totalmente compatíveis com IPv6. Os desenvolvedores que criaram ou usam a sua própria pilha de rede devem querer verificar novamente se existem outras considerações atenuantes. Veja a seguir algumas informações adicionais da Apple:

*Se estiver desenvolvendo um aplicativo no lado do cliente usando APIs de rede de alto nível, como NSURLSession e as estruturas CFNetwork, e se a conexão for feita pelo nome, não será necessário alterar nada para que o aplicativo funcione com endereços IPv6.* Para obter mais informações, consulte [Suporte a redes IPv6 DNS64/NAT64](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1).


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### O que são Métricas de ciclo de vida?

As Métricas de ciclo de vida são métricas “predefinidas” que são automaticamente coletadas quando o SDK é implementado pela primeira vez no aplicativo. Para obter mais informações, consulte [Métricas de ciclo de vida (Android)](/help/android/metrics.md) e [Métricas de ciclo de vida (iOS)](/help/ios/metrics.md).

### Como posso solucionar problemas de regras de processamento?

Para obter mais informações, consulte [Dicas e truques das regras de processamento](https://docs.adobe.com/content/help/pt-BR/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html).

### É possível enviar meus dados de análise para vários conjuntos de relatórios?

Sim. Os SDKs fornecem a capacidade de enviar dados para vários conjuntos de relatórios do Adobe Analytics. Para capturar dados em vários conjunto de relatórios usando uma solicitação de imagem, defina as várias IDs de conjuntos de relatórios no campo **[!UICONTROL rsids]** na seção **[!UICONTROL analytics]** no arquivo `ADBMobileConfig.json`, delimitadas por vírgulas e sem espaços. Para obter mais informações, consulte [Configuração do JSON do ADBMobile](/help/ios/configuration/json-config/json-config.md).

### Como as visitas do Mobile são diferentes das inicializações?

Uma inicialização é medida pelo SDK quando um usuário abre o aplicativo pela primeira vez ou retorna ao aplicativo depois de ficar fora dele por mais tempo do que o valor de tempo limite especificado. O tempo limite típico é de 5 minutos (300 segundos) no campo **[!UICONTROL lifecycleTimeout]**, que está localizado no arquivo `ADBMobileConfig.json`. Uma visita é um cálculo do lado do servidor feito pelo Adobe Analytics e tem por base a primeira e a última ocorrência de dados enviada pelo SDK, sem exceder o tempo limite da visita. Normalmente, os tempos limite da sessão são definidos em 30 minutos para um conjunto de relatórios. Embora as visitas sejam provenientes de análises da Web tradicionais, essas ocorrências ainda fornecem informações valiosas sobre como os usuários entram e saem do aplicativo.

## Mensagens {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### Existem limitações de tamanho ou de outro tipo em notificações de push?

As mensagens de notificação de push têm um limite de 140 caracteres. Não há limites para quantas notificações podem ser enviadas ou programadas ou quantas vezes elas são enviadas.

### Cargas personalizadas para notificações de push são aceitas?

Sim, fornecemos uma carga de push personalizada que pode ser codificada no JSON. As cargas do Android e do iOS estão restritas a 4 KB e 2 KB, respectivamente. Essas cargas são enviadas para o aplicativo por meio de uma notificação de push ou local. Para obter mais informações, consulte [Experiência: mensagem por push](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Existem limitações de tamanho em mensagens no aplicativo?

As mensagens no aplicativo publicadas e ativas criadas no Adobe Mobile Services são hospedadas em um servidor com uma restrição de tamanho de 15 MB por conjunto de relatórios do aplicativo. Embora essa restrição se aplique ao conteúdo da mensagem e aos recursos hospedados com a Adobe, não há restrições sobre a quais recursos a mensagem no aplicativo pode se referir em outros hosts ou aqueles dentro do aplicativo.

### Posso usar meu próprio HTML para mensagens no aplicativo?

Sim, oferecemos suporte a HTML personalizado para suas mensagens no aplicativo. Para obter mais informações, consulte [Experiência: mensagem no aplicativo](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

### Quais acionadores posso usar para enviar notificações de push ou mensagens no aplicativo?

Os profissionais de marketing podem escolher quaisquer dados ou eventos do Analytics enviados como acionadores para exibir mensagens no aplicativo. As mensagens no aplicativo usam acionadores que ocorrem localmente no dispositivo. Se vários acionadores forem escolhidos, todos devem acontecer na mesma ocorrência para que a mensagem seja exibida. Para obter mais informações, consulte [Experiência: mensagem no aplicativo](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

As mensagens de push são enviadas usando segmentos do Adobe Analytics pré-existentes ou segmentos personalizados que podem ser criados no dados de histórico do Analytics já coletados. Para obter mais informações, consulte [Experiência: mensagem por push](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Por que ocorre um erro quando digito o nome da mensagem no aplicativo, da mensagem por push e do link de marketing?

Você não pode usar a mesma mensagem no aplicativo e de push nem marcar o nome do link em vários aplicativos que usam o mesmo conjunto de relatórios principal ou VRS. Para resolver esse problema, insira outro nome para a mensagem no aplicativo, a mensagem por push ou o link de marketing.

## Localização {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### Existe um limite para os meus pontos de interesse (POIs)?

Não há restrição específica, mas para um desempenho ideal e devido a restrições de memória no dispositivo do usuário, recomendamos criar ou carregar no máximo 5000 POIs.

## Aquisição {#section_B37F1129CD5843E890D0E54179455357}

### Posso atribuir campanhas a atividades no aplicativo?

Sim. O Adobe Mobile Services pode ajudar você a criar truques de marketing que ajudam a promover e direcionar o tráfego para seus aplicativos e vincular campanhas de aquisição a análises e conversões no aplicativo. Para obter mais informações, consulte [Aquisição](/help/using/acquisition-main/acquisition-main.md).

### Como posso configurar links para adquirir e rastrear novos usuários do aplicativo?

É possível criar links de marketing que encaminham o usuário para baixar aplicativos na App Store da Apple e no Google Play. Esses links permitem atribuir seus eventos de sucesso aos downloads. Para obter mais informações, consulte [Criador de links de marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).