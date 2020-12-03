---
description: Você pode aproveitar o Adobe Target em seus aplicativos TVML/TVJS fazendo substituições diretas em seus arquivos .xml. Designe áreas de sua página para serem substituídas pelo conteúdo do Público alvo usando o elemento XML ADBTarget personalizado.
seo-description: Você pode aproveitar o Adobe Target em seus aplicativos TVML/TVJS fazendo substituições diretas em seus arquivos .xml. Designe áreas de sua página para serem substituídas pelo conteúdo do Público alvo usando o elemento XML ADBTarget personalizado.
seo-title: Adobe Target para TVML/TVJS
title: Adobe Target para TVML/TVJS
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 70%

---


# Adobe Target para TVML/TVJS{#adobe-target-for-tvml-tvjs}

Você pode aproveitar o Adobe Target em seus aplicativos TVML/TVJS fazendo substituições diretas em seus arquivos .xml. Designe áreas de sua página para serem substituídas pelo conteúdo do Público alvo usando o elemento XML ADBTarget personalizado.

>[!IMPORTANT]
>
>Antes de usar o elemento `ADBTarget` em suas páginas TVML, você deve configurar o aplicativo TVML/TVJS para usar o tvOS SDK. Para obter mais informações, consulte [Implementação da Apple TV com tvOS](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md).

## Introdução {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Identifique o arquivo `.xml` no qual você deseja usar a localização do seu Target.
1. Adicione um elemento `ADBTarget` ao arquivo como filho do elemento `<document>`.
1. Se o Target não encontrar a localização da Mbox, ou se atingir o tempo limite, o valor entre as tags `<ADBTarget>` e `</ADBTarget>` será usado como conteúdo padrão.

## Configurar a Mbox no Target {#section_F2DA140C34B0421D976046F825B23123}

O conteúdo retornado do Target substitui todo o conteúdo entre `<ADBTarget>` e `</ADBTarget>`, incluindo as tags `ADBTarget`.

>[!TIP]
>
>É necessário planejar o item que será substituído.

Seu caso de uso pode ser tão simples como substituir um valor da cadeia de caracteres em um rótulo ou tão complexo como substituir uma página inteira.

## Configurar o elemento ADBTarget {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

No elemento `ADBTarget`, você deve fornecer o nome da na propriedade `mbox`mbox. Opcionalmente, é possível adicionar propriedades personalizadas à solicitação no formato `customParameterName="customParameterValue"`.

* **`mbox`**

   Nome da localização da Mbox.

   * Tipo de propriedade: String
   * Esta propriedade é obrigatória.

* **`id`**

   A ID do pedido.

   * Tipo de propriedade: String
   * Esta propriedade **não** é obrigatória.

* **`total`**

   O total do pedido.

   * Tipo de propriedade: String
   * Esta propriedade **não** é obrigatória.

* **`purchasedProductIds`**

   Uma lista separada por vírgulas de IDs de produtos adquiridos para este pedido.

   * Esta é a amostra de código para essa propriedade:


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * Tipo de propriedade: String
   * Esta propriedade **não** é obrigatória.

* **`mboxParameters`**

   Uma lista de pares de valores chave para `mboxParameters`. Cada entrada nessa sequência é separada por um ponto e vírgula, e os valores-chave são separados por dois pontos.

   * Esta é a amostra de código para essa propriedade:

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * Tipo de propriedade: String
   * Esta propriedade **não** é obrigatória.

* **`customParameterName`**

   O valor dessa propriedade é `customParameterValue`.

   * Tipo de propriedade: String
   * Esta propriedade **não** é obrigatória.


## Exemplos {#section_6D6D6E8C7FE147168FC30D83CBC06985}

### Exemplo 1

O seguinte exemplo usa um elemento `ADBTarget` na página `LandingPage.xml.js` para substituir os conteúdos de um alerta:

#### Configurar Target

Suponha que você tenha um local da Mbox chamado `landingPage` e o conteúdo da oferta esteja configurado para ser o seguinte:

```objective-c
<title>My cool landing page</title> 
<description>Thanks for coming to my page</description> 
```

#### Configurar landingPage.xml.js

* Esta é a configuração para landingPage.xml.js:

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* Se a solicitação para o Público alvo for bem-sucedida e o conteúdo da oferta for retornado, sua página resultará em:

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* Se o servidor do Público alvo não puder ser acessado ou a solicitação expirar, sua página resultará em:

   ```objective-c
   <alertTemplate> 
       <title>TargetTestPage</title> 
       <description>Load fail or timeout (defaultContent)</description> 
   </alertTemplate>
   ```

### Exemplo 2

O exemplo a seguir ilustra como adicionar dados personalizados ao elemento `ADBTarget`. Esse método permite que você crie experiências condicionais e ofereça conteúdo para essa localização da Mbox no Target:

```objective-c
<alertTemplate> 
    <ADBTarget mbox="landingPage" customData="custom data" moreCustomData="more custom data"> 
        <title>TargetTestPage</title> 
        <description>Load fail or timeout (defaultContent)</description> 
    </ADBTarget>  
</alertTemplate>
```
