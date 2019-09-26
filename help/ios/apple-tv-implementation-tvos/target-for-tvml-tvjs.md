---
description: Você pode alavancar o Adobe Target em seus aplicativos TVML/TVJS fazendo substituições diretas em seus arquivos .xml. Atribua áreas da sua página para serem substituídas pelo conteúdo do Target usando o elemento ADBTarget XML personalizado.
seo-description: Você pode alavancar o Adobe Target em seus aplicativos TVML/TVJS fazendo substituições diretas em seus arquivos .xml. Atribua áreas da sua página para serem substituídas pelo conteúdo do Target usando o elemento ADBTarget XML personalizado.
seo-title: Adobe Target para TVML/TVJS
title: Adobe Target para TVML/TVJS
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Adobe Target para TVML/TVJS{#adobe-target-for-tvml-tvjs}

Você pode alavancar o Adobe Target em seus aplicativos TVML/TVJS fazendo substituições diretas em seus arquivos .xml. Atribua áreas da sua página para serem substituídas pelo conteúdo do Target usando o elemento ADBTarget XML personalizado.

>[!IMPORTANT]
>
>Before using the `ADBTarget` element in your TVML pages, you must configure your TVML/TVJS app to use the tvOS SDK. Para obter mais informações, consulte Implementação da [Apple TV com tvOS](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md).

## Introdução {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Identify the `.xml` file in which you want to use your Target location.
1. Add an `ADBTarget` element to the file as a child of the `<document>` element.
1. If Target fails to find your Mbox location, or it times out, the value between your `<ADBTarget>` and `</ADBTarget>` tags is used as default content.

## Configure your mbox in Target {#section_F2DA140C34B0421D976046F825B23123}

The returned content from Target replaces all content between `<ADBTarget>` and `</ADBTarget>`, including both `ADBTarget` tags.

>[!TIP]
>
>Você deve planejar o que deseja substituir de acordo.

Seu caso de uso pode ser tão simples como substituir um valor da cadeia de caracteres em um rótulo ou tão complexo como substituir uma página inteira.

## Configurar o elemento ADBTarget {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

No elemento `ADBTarget`, você deve fornecer o nome da na propriedade `mbox`mbox. You can optionally add custom properties to your request in the `customParameterName="customParameterValue"` format.

* **`mbox`**

   Nome da localização da Mbox.

   * Tipo de propriedade: String
   * Essa propriedade é obrigatória.

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

   * Esta é a amostra de código para esta propriedade:


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * Tipo de propriedade: String
   * Esta propriedade **não** é obrigatória.

* **`mboxParameters`**

   Uma lista de pares de valores chave para `mboxParameters`. Cada entrada nessa string é separada por um ponto-e-vírgula, e os valores-chave são separados por dois-pontos.

   * Esta é a amostra de código para esta propriedade:

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

* Esta é a configuração de landingPage.xml.js:

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* Se a solicitação ao Target for bem-sucedida e o conteúdo da sua oferta for retornado, sua página resultará em:

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* Se o servidor Target não puder ser alcançado ou a solicitação expirar, sua página resultará em:

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
