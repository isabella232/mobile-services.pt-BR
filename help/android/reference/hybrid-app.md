---
description: Se o aplicativo abrir o conteúdo da internet móvel, certifique-se de que os visitantes não sejam identificados conforme se movem entre a internet nativa e móvel.
seo-description: Se o aplicativo abrir o conteúdo da internet móvel, certifique-se de que os visitantes não sejam identificados conforme se movem entre a internet nativa e móvel.
seo-title: Rastreamento de visitantes entre um aplicativo e a internet móvel
solution: Experience Cloud,Analytics
title: Rastreamento de visitantes entre um aplicativo e a internet móvel
topic: Desenvolvedor e implementação
uuid: 073572e4-4c55-4b27-b4a7-e4349ccde7bf
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Rastreamento de visitantes entre um aplicativo e a internet móvel {#visitor-tracking-between-an-app-and-mobile-web}

Se o aplicativo abrir o conteúdo da internet móvel, certifique-se de que os visitantes não sejam identificados conforme se movem entre a internet nativa e móvel.

## IDs de visitantes em aplicativos

O Android SDK gera uma ID de visitante único quando o aplicativo é instalado. Esta ID é armazenada na memória persistente no dispositivo móvel, é enviada com cada ocorrência e é removida apenas quando o usuário desinstala o aplicativo.

>[!TIP]
>
>As IDs de visitante do aplicativo persistem em todas as atualizações.

## IDs de visitantes na internet móvel

As implementações usuais da internet móvel usam o mesmo Analytics padrão `s_code.js` ou `AppMeasurement.js` usado em sites do desktop. As bibliotecas JavaScript têm seus próprios métodos de geração de IDs de visitante único, o que faz com que uma ID de visitante diferente seja gerada ao abrir conteúdo da Web móvel do seu aplicativo.

## Implementação de rastreamento de visitantes entre um aplicativo e a internet móvel {#section_1755BCCFD42D456EB2319141030FDDFF}

Para usar a mesma ID de visitante no aplicativo e na Web móvel:

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o arquivo de configuração ao projeto IntelliJ IDEA ou Eclipse* na [Implementação principal e ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Para anexar informações do visitante ao URL que está sendo usado para abrir a exibição da Web, chame `visitorAppendToURL`:

   ```java
   String urlString = "https://www.mydomain.com/index.php"; 
   String urlStringWithVisitorData = Visitor.appendToURL(urlString); 
   Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
   startActivity(browserIntent);
   ```

   Como alternativa, a partir da versão 4.16.0 do SDK, é possível chamar `Visitor.getUrlVariablesAsync` e gerar seu próprio URL:

   ```java
   final String urlString = "https://www.mydomain.com/index.php"; 
   Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
       @Override 
       public void call(String urlVariables) { 
           final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
           final Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
           startActivity(browserIntent); 
       } 
   });
   ```

O código do serviço de ID no domínio de destino extrai a MID do URL em vez de enviar uma solicitação de nova ID para a Adobe. O código usa o que foi fornecido em MID para rastrear o visitante.

Em ocorrências do conteúdo da internet móvel, verifique se o parâmetro `mid` existe em cada ocorrência e de que este valor corresponde ao parâmetro `mid` enviado por esse código do aplicativo.

## Resolução de problemas do rastreamento de visitantes {#section_9B641F8569E34A089C52AA28EA4C891D}

### Não vejo `Visitor.appendToURL`.

Verifique se o SDK da Adobe que está empacotada no aplicativo principal é versão 4.12.0 ou superior.

**Não vejo as Adobe IDs no meu URL.**

* Verifique o seguinte:
   * A cadeia de caracteres do URL que foi usada para abrir a exibição da Web foi gerada por `Visitor.appendToURL(urlString)`.
   * As Adobe IDs estão codificadas. 
Para assegurar que as IDs sejam anexadas ao URL que está sendo aberto, verifique se o parâmetro de consulta `adobe_mc` aparece no URL.

### Meu `mid` não é idêntico no aplicativo e na exibição da Web.

* Verifique o seguinte:

   * A cadeia de caracteres de URL que está sendo usada para abrir a exibição da Web foi gerada por `Visitor.appendToURL(urlString)`.
   * A cadeia de caracteres do URL contém parâmetros da Adobe.

      A cadeia de caracteres deve conter `adobe_mc="SAMPLE_ID_DATA"`, em que o `"SAMPLE_ID_DATA"` contém as IDs geradas no Adobe Mobile SDK.
   * O `VisitorAPI.js` é versão 1.7.0 ou superior.

Caso essas etapas de solução de problemas não resolvam os mesmos, entre em contanto com o Adobe Experience Care.

>[!IMPORTANT]
>
>Para permitir que a Adobe valide a implementação, é necessário compartilhar um aplicativo de amostra e o site relacionado.

