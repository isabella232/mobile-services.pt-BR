---
description: As seguintes informações ajudam a redirecionar um link de campanha de aquisição de legado com base em uma impressão digital do dispositivo.
seo-description: As seguintes informações ajudam a redirecionar um link de campanha de aquisição de legado com base em uma impressão digital do dispositivo.
seo-title: Teste da aquisição de legado
solution: Experience Cloud,Analytics
title: Teste da aquisição de legado
uuid: e0591f4a-e26b-4fe4-97c1-a6831a926fa5
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Teste de aquisição de legado {#testing-legacy-acquisition}

As seguintes informações ajudam a redirecionar um link de campanha de aquisição de legado com base em uma impressão digital do dispositivo.

Se o aplicativo móvel ainda não estiver no Google Play, você pode selecionar qualquer aplicativo móvel como destino ao criar o link da campanha. Isso não afeta a capacidade de testar o link de aquisição, afeta somente o aplicativo para o qual você é redirecionado pelo servidor de aquisição após clicar no link.

1. Navegue até **[!UICONTROL Usar links de aquisição de legado]** no Adobe Mobile Services e gere um URL de campanha de aquisição.

   Para obter mais informações, consulte [Usar links de aquisição de legado](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).

1. No dispositivo móvel no qual você instalará o aplicativo, clique no link gerado.

   Os servidores da Adobe ( `c00.adobe.com` ) armazenam a impressão digital e redirecionam para a App Store. O aplicativo não precisa ser baixado para testes.

1. No mesmo dispositivo móvel que você usou na etapa 2, inicie o aplicativo pela primeira vez.

   A maneira mais fácil de garantir que isso aconteça é excluir e instalar o aplicativo novamente.

Lembre-se das seguintes informações:

* O servidor de aquisição fornece uma correspondência de atribuição baseada no endereço IP e nas informações agente-usuário gravadas aos cliques em links (etapa 2) e quando o aplicativo é iniciado (etapa 3).
* Ao usar ferramentas de monitoramento HTTP, as ocorrências enviadas pelo aplicativo podem ser monitoradas para fornecer a verificação da atribuição de aquisição.

>[!TIP]
>
>As variações no agente-usuário enviado podem causar falha na atribuição.
