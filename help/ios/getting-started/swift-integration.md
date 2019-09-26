---
description: O SDK do Adobe Mobile do iOS pode ser perfeitamente integrado a um projeto Swift, usando o recurso Misturar e combinar na biblioteca de desenvolvedor do iOS.
seo-description: O SDK do Adobe Mobile do iOS pode ser perfeitamente integrado a um projeto Swift, usando o recurso Misturar e combinar na biblioteca de desenvolvedor do iOS.
seo-title: Integração Swift
solution: Marketing Cloud,Analytics
title: Integração Swift
topic: Desenvolvedor e implementação
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Swift integration {#swift-integration}

O SDK do Adobe Mobile do iOS pode ser perfeitamente integrado a um projeto Swift, usando o recurso Misturar e combinar na biblioteca de desenvolvedor do iOS.

Para obter mais informações, consulte Interoperabilidade [de](https://developer.apple.com/documentation/swift#2984801.html)linguagem.

Por exemplo, usando o método de cabeçalho de ligação conforme descrito na documentação, é possível importar o arquivo de cabeçalho do SDK do iOS do Adobe Mobile:

```
#import “ADBMobile.h”
```

Para acessar os métodos do SDK em seus arquivos Swift, use o seguinte formato:

```
ADBMobile.{methodname}
```

