---
title: Compilerfehler C3463
ms.date: 11/04/2016
f1_keywords:
- C3463
helpviewer_keywords:
- C3463
ms.assetid: 153efcc0-085c-4615-84ea-d22942618bdf
ms.openlocfilehash: a0c7772291085bcd872cbc1ca23b79d2fa829ad9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222345"
---
# <a name="compiler-error-c3463"></a>Compilerfehler C3463

"Typ": Der Typ ist im implements-Attribut nicht zulässig.

Ein ungültiger Typ wurde an das [implements](../../windows/implements-cpp.md) -Attribut übergeben. Beispielsweise können Sie eine Schnittstelle an `implements`übergeben, Sie können aber keinen Zeiger an eine Schnittstelle übergeben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3463 generiert:

```
// C3463.cpp
// compile with: /c
#include <windows.h>
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface X {};

typedef X* PX;

[ coclass, uuid("00000000-0000-0000-0000-000000000002"), implements(interfaces=PX) ]   // C3463
// try the following line instead
// [ coclass, uuid("00000000-0000-0000-0000-000000000002"), implements(interfaces=X) ]
class CMyClass : public X {};
```