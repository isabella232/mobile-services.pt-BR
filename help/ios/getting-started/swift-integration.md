---
description: O SDK do Adobe Mobile do iOS pode ser perfeitamente integrado a um projeto Swift, usando o recurso Misturar e combinar na biblioteca de desenvolvedor do iOS.
seo-description: O SDK do Adobe Mobile do iOS pode ser perfeitamente integrado a um projeto Swift, usando o recurso Misturar e combinar na biblioteca de desenvolvedor do iOS.
seo-title: Integração Swift
solution: Experience Cloud,Analytics
title: Integração Swift
topic: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 100%

---


# Integração Swift {#swift-integration}

O SDK do Adobe Mobile do iOS pode ser perfeitamente integrado a um projeto Swift, usando o recurso Misturar e combinar na biblioteca de desenvolvedor do iOS.

Para obter mais informações, consulte [Interoperacionalidade de idioma](https://developer.apple.com/documentation/swift#2984801.html).

Por exemplo, usando o método de cabeçalho de ponte conforme descrito na documentação, você pode importar o arquivo de cabeçalho do SDK do iOS do Adobe Mobile:

```
#import “ADBMobile.h”
```

Para acessar métodos do SDK em seus arquivos Swift, use o seguinte formato:

```
ADBMobile.{methodname}
```

