---
description: O SDK do Adobe Mobile do iOS pode ser perfeitamente integrado a um projeto Swift, usando o recurso Misturar e combinar na biblioteca de desenvolvedor do iOS.
solution: Experience Cloud,Analytics
title: Integração Swift
topic-fix: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
exl-id: 3c1a2e28-53b0-4128-a5d9-d2403885098d
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 100%

---

# Integração Swift {#swift-integration}

O SDK do Adobe Mobile do iOS pode ser perfeitamente integrado a um projeto Swift, usando o recurso Misturar e combinar na biblioteca de desenvolvedor do iOS.

Para obter mais informações, consulte [Interoperacionalidade de idioma](https://developer.apple.com/documentation/swift#2984801.html).

Por exemplo, usando o método de cabeçalho de ponte conforme descrito na documentação, você pode importar o arquivo de cabeçalho do SDK do iOS do Adobe Mobile:

```
#import "ADBMobile.h"
```

Para acessar métodos do SDK em seus arquivos Swift, use o seguinte formato:

```
ADBMobile.{methodname}
```
