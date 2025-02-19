---
title: Zeichenoperator (#@)
ms.date: 11/04/2016
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: c9acc9b9872e096cd441b950632c341e975fecb8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403528"
---
# <a name="charizing-operator-"></a>Zeichenoperator (#@)
**Microsoft-spezifisch**

Der Zeichenoperator kann nur mit Argumenten von Makros verwendet werden. Wenn `#@` steht einen formalen Parameter in der Definition des Makros ist das tatsächliche Argument in einfache Anführungszeichen eingeschlossen und als Zeichen behandelt wird, wenn das Makro erweitert wird. Zum Beispiel:

```
#define makechar(x)  #@x
```

führt dazu, dass die Anweisung

```
a = makechar(b);
```

erweitert wird auf

```
a = 'b';
```

Das einfache Anführungszeichen kann nicht mit dem Zeichenoperator verwendet werden.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Präprozessoroperatoren](../preprocessor/preprocessor-operators.md)