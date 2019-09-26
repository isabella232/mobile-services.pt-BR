---
description: É possível definir e configurar as opções de público-alvo para mensagens de push, incluindo as opções de intervalo de data, os segmentos do Analytics e os segmentos personalizados.
keywords: mobile
seo-description: É possível definir e configurar as opções de público-alvo para mensagens de push, incluindo as opções de intervalo de data, os segmentos do Analytics e os segmentos personalizados.
seo-title: Público-alvo Definir e configurar segmentos de público-alvo para mensagens de push
solution: Marketing Cloud,Analytics
title: Audience  Define and Configure Audience Segments for Push Messages
topic: Métricas
uuid: efd410e7-3b6c-4cf4-a26f-b11688adc491
translation-type: tm+mt
source-git-commit: f28ea0db13b8d8f209d7521d1f61f1c290e688aa

---


# Público: mensagens de push{#audience-define-and-configure-audience-segments-for-push-messages}

É possível definir e configurar as opções de público-alvo para mensagens de push, incluindo as opções de intervalo de data, os segmentos do Analytics e os segmentos personalizados.

## Define audience segments {#section_7C4D2393CF7441959FE2381A02867CAC}

Quando um segmento de público-alvo das mensagens de push é criado, o segmento pode envolver usuários de um ou mais aplicativos porque os conjuntos de relatórios ou conjuntos de relatórios virtuais podem conter dados de um ou mais aplicativos. Para obter mais informações sobre conjuntos de relatórios virtuais, consulte [Virtual report suites](/help/using/manage-apps/c-mob-vrs.md).

No Adobe Mobile Services, os profissionais de marketing podem apenas enviar para um aplicativo por plataforma. Se os profissionais de marketing tentarem enviar para segmentos que contêm usuários de vários aplicativos, será exibido um aviso afirmando que o processo pode resultar em falhas de envio graves e na possível inclusão de usuários na lista negra. Se você tiver uma falha de envio, consulte *Resolução de falhas de envio* em [Troubleshooting push messaging](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).

Para usar os dados do Audience Manager na definição do seu segmento, consulte [Análise de público-alvo](https://docs-author-stg.corp.adobe.com/content/help/en/analytics/integration/audience-analytics/mc-audiences-aam.html).

>[!IMPORTANT]
>
>If app users are blacklisted, marketers can **never** send push messages to those affected users again.

Se você selecionar um segmento de público-alvo que contém usuários em vários aplicativos, poderá ver o seguinte alerta:

![nome de vários aplicativos](assets/multiple_appname.png)

The app name is based on the pared down version of the appId, which is automatically sent to Adobe Analytics by the Mobile Services SDK in the `<app name> <version number> (<bundle id>)` format.

>[!TIP]
>
>O número da versão é opcional.

São removidos até 6 conjuntos de números para a versão e até 5 conjuntos de números para a ID do pacote.

Por exemplo:

* `Bea[rd]cons 1.0 (123)` aparecerá como `Bea[rd]cons`
* `Bea[rd]cons 1.2 (1.2)` aparecerá como `Bea[rd]cons`
* `Bea[rd]cons 1.2.3.4.5.6.7 (1111)` aparecerá como `Bea[rd]cons .7`
* `Bea[rd]cons 1.2.3. (1.2.3.4.5.6)` aparecerá como `Bea[rd]cons (.6)`

Para continuar a enviar a mensagem de push para os aplicativos listados, marque a caixa de seleção **Sim, eu desejo continuar.** e clique em **[!UICONTROL Enviar]**.

## Práticas recomendadas

Estas são algumas das práticas recomendadas para lembrar:

* Para reduzir a confusão, **evite** definir conjuntos de relatórios virtuais de aplicativo móvel que tenham dados de vários aplicativos.
* Use uma ID de aplicativo exclusiva como parte de um segmento de público-alvo **sempre** que desejar enviar uma mensagem de push.
Isso garante que as notificações por push sejam enviadas para um segmento de público-alvo que pertence a **apenas** um aplicativo.

### Exemplos

Alguns exemplos para ajudá-lo a entender como definir segmentos corretamente:

**Sim**: o profissional de marketing fornece certificados de push das versões para iOS e Android de um aplicativo, por exemplo, para o Adobe Photoshop. O profissional de marketing pode enviar uma notificação por push para um segmento de usuário que abrange as duas plataformas.

**Não**: os profissionais de marketing fornecem certificados de push das versões para iOS e Android de um aplicativo, por exemplo, para o Adobe Photoshop. Se o profissional de marketing criar e enviar um push para um segmento de *todos os usuários ativos nos últimos 30 dias*, apenas os usuários do aplicativo Adobe Photoshop para iOS e Android receberão o push e todos os usuários desses aplicativos serão adicionados à lista negra. Para obter mais detalhes, consulte *Resolução de falhas de mensagem de push* em [Solucionar problemas de mensagens de push](/help/using/in-app-messaging/t-create-push-message/c-troubleshooting-push-messaging.md).

## Configure audience segments {#section_A92C60885A30421B8150820EC1CCBF13}

1. Vá para a página Público-alvo para obter uma nova mensagem de push.

   For more information, see [Create a push message](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   As you configure the audience options, remember the following **important** information:

   * O **[!UICONTROL Público-alvo estimado de aceitação]** é o número de dispositivos que combinam o segmento do Adobe Analytics **e** o número de dispositivos de aceitação.

      É possível exibir uma estimativa do número de usuários nos segmentos selecionados que aceitaram receber mensagens e receberão a mensagem de push. O número total de usuários do aplicativo é exibido abaixo da estimativa, independentemente do status da aceitação.

   * O **[!UICONTROL Total]é o número de dispositivos que correspondem ao segmento do Adobe Analytics.**

   * Push messages are sent to the devices that are part of a defined Adobe Analytics segment **and** that have opted-in for push messages.

      Isso significa que o SDK enviou um valor `True` para a eVar de aceitação de mensagens de push.

   * Mesmo que o dispositivo tenha um token de dispositivo válido, a menos que o Adobe Analytics tenha definido o sinalizador de aceitação, a mensagem não será enviada para o dispositivo.

   * Para obter mais informações sobre como solucionar problemas de mensagens de push, consulte o seguinte:

      * [Push messaging in iOS](https://docs.adobe.com/content/help/en/mobile-services/ios/messaging-ios/push-messaging/push-messaging.html)

      * [Push messaging in Android](https://docs.adobe.com/content/help/en/mobile-services/android/messaging-android/push-messaging/push-messaging.html)

1. Digite informações nos seguintes campos:

   * **[!UICONTROL Durante os]**

      Especifique o período de tempo que será usado para o público-alvo estimado. Na lista suspensa **[!UICONTROL Durante os], selecione uma opção:**

   * **[!UICONTROL Últimos]** permite selecionar um período relativo (por exemplo, os últimos 7 dias, os últimos 30 dias ou os últimos 60 dias) a partir do momento em que a mensagem é agendada para envio.

      Por exemplo, se você selecionar os últimos 30 dias e agendar a mensagem de push para 31 de outubro, o público-alvo estimado será o número de usuários que aceitaram receber as mensagens de push nos 30 dias anteriores a 31 de outubro.

   * **[!UICONTROL Intervalo estático]** permite selecionar um intervalo estático ao escolher as datas de início e de término para o intervalo do público-alvo estimado.

      Usando o exemplo anterior, se você selecionar um intervalo de datas que começa em 1° de outubro e termina em 15 de outubro, mas agendar a mensagem de push para 31 de outubro, o público-alvo estimado será o número de usuários que aceitaram receber mensagens de push no intervalo de datas estático que você especificou (1° de outubro a 15 de outubro).

   * **[!UICONTROL Segmentos do Analytics]**

      Select an existing Adobe Analytics segment from the drop-down list. For more information, see [Build segments](https://docs.adobe.com/content/help/en/analytics/components/segmentation/segmentation-workflow/seg-build.html).

   * **[!UICONTROL Segmentos personalizados]**

      Select a metric or variable from the drop-down list (for example, **[!UICONTROL Days Since Last Use]** or **[!UICONTROL Point of Interest]**) and configure the filter as desired. Por exemplo, o segmento personalizado a seguir aponta os usuários que possuem um telefone celular com o iOS e estão na região da Califórnia (Estados Unidos).
   >[!IMPORTANT]
   >
   >In the **[!UICONTROL Create Audience]** section, if you click **[!UICONTROL And]**, a dialog box appears that reminds you to ensure that each app that is listed **must** have a valid certificate. If you clicked **[!UICONTROL Or]**, the default dialog box appears. For more information about valid certificates and report suites, see [Virtual report suites](/help/using/manage-apps/c-mob-vrs.md).
