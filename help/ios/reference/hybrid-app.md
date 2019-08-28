---
description: Se o seu aplicativo abrir conteúdo da Web móvel, você precisa garantir que os visitantes não sejam identificados separadamente conforme se moverem entre a Web móvel e nativa.
seo-description: Se o seu aplicativo abrir conteúdo da Web móvel, você precisa garantir que os visitantes não sejam identificados separadamente conforme se moverem entre a Web móvel e nativa.
seo-title: Rastreamento de visitantes entre um aplicativo e a Web móvel
solution: Marketing Cloud, Analytics
title: Rastreamento de visitantes entre um aplicativo e a Web móvel
topic: Desenvolvedor e implementação
uuid: 2 d 951 de 6-3954-4379-a 4 ff -99 b 9695 b 9869
translation-type: tm+mt
source-git-commit: 9257d6b6c2c14d0422cda65fcc9c677ac5ac47a9

---


# Visitor tracking between an app and mobile web  {#visitor-tracking-between-an-app-and-mobile-web}

Se o seu aplicativo abrir conteúdo da Web móvel, você precisa garantir que os visitantes não sejam identificados separadamente conforme se moverem entre a Web móvel e nativa.

## IDs de visitante em aplicativos

O SDK do iOS gera uma ID de visitante único quando um aplicativo é instalado. Esta ID é armazenada na memória persistente no dispositivo móvel e é enviada com cada ocorrência. Esta ID é removida somente quando o usuário desinstala o aplicativo.

>[!TIP]
>
>As IDs de visitante do aplicativo continuam por meio das atualizações.

## IDs de visitante na Web móvel

As implementações usuais da internet móvel usam o mesmo Analytics padrão `s_code.js` ou `AppMeasurement.js` usado em sites do desktop. As bibliotecas JavaScript têm seus próprios métodos de geração de IDs de visitante único, o que faz com que uma ID de visitante diferente seja gerada ao abrir conteúdo da Web móvel do seu aplicativo.

Para usar a mesma ID de visitante no aplicativo e na Web móvel e enviar a ID de visitante do aplicativo para a Web móvel no URL:

## Implement visitor tracking between an app and mobile web {#section_EDC91D6C67AD43999227707C2769C65D}

1. Adicione a biblioteca ao projeto e implemente o ciclo de vida.

   Para obter mais informações, consulte *Adicionar o SDK e o Arquivo de configuração ao projeto* na [Implementação principal e no ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Para anexar informações do visitante ao URL que está sendo usado para abrir a exibição da Web, chame `visitorAppendToURL`:

   ```objective-c
   NSURL *url = [NSURL URLWithString:@”https://www.mydomain.com/index.php"]; 
   NSURL *urlWithVisitorData = [ADBMobile visitorAppendToURL:url]; 
   [[UIApplication sharedApplication] openURL:urlWithVisitorData];
   ```

   Como alternativa, a partir da versão 4.16.0 do SDK, é possível chamar `visitorGetUrlVariablesAsync:` e gerar seu próprio URL:

   ```objective-c
   NSString *urlString = @"https://www.mydomain.com/index.php"; 
   [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
       NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
       NSURL *urlWithVisitorData = [NSURL URLWithString:urlStringWithVisitorData]; 
       [[UIApplication sharedApplication] openURL:urlWithVisitorData options:@{} completionHandler:^(BOOL success) { 
           // handle openURL success 
       }]; 
   }];
   ```

O código do serviço de ID no domínio de destino extrai a MID do URL em vez de enviar uma solicitação de nova ID para a Adobe. O código do serviço de ID na página de destino utiliza a MID passada para rastrear o visitante.

Nas ocorrências do conteúdo da Web móvel, verifique se o parâmetro `mid` está presente em cada ocorrência e se esse valor corresponde ao `mid` que está sendo enviado pelo código do aplicativo.

## Solucionar problemas do rastreamento de visitantes {#section_C070AE85E3CE4E9893FD4F40E73F2C92}

### I do not see `[ADBMobile visitorAppendToURL:]`.

Verifique se o SDK da Adobe que está empacotada no aplicativo principal é versão 4.12.0 ou superior.

### Não vejo as Adobe IDs no meu URL.

Verifique o seguinte:

* A cadeia de caracteres de URL que está sendo usada para abrir a exibição da Web foi gerada por  `[ADBMobile visitorAppendToURL:]`

* As Adobe IDs estão codificadas.

   To verify that IDs are appended to the URL that is being opened, look for the `adobe_mc` query parameter.

### O "mid" do meu aplicativo não é idêntico ao da minha exibição da Web.*

Verifique o seguinte:

* A cadeia de caracteres de URL que está sendo usada para abrir a exibição da Web foi gerada por `[ADBMobile visitorAppendToURL:]`

   A cadeia de caracteres do URL contém parâmetros da Adobe.

   The string should contain `adobe_mc="SAMPLE_ID_DATA"` where `"SAMPLE_ID_DATA"` contains the IDs that are generated in the Adobe Mobile SDK.

* O `VisitorAPI.js` é versão 1.7.0 ou superior.

Se essas etapas de solução de problemas não resolverem seus problemas, entre em contato com o Adobe Client Care; esteja preparado para compartilhar um aplicativo de exemplo e o site associado para que a Adobe possa validar a implementação.
