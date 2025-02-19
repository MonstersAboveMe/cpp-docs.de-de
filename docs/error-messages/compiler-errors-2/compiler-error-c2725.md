---
title: Compilerfehler C2725
ms.date: 11/04/2016
f1_keywords:
- C2725
helpviewer_keywords:
- C2725
ms.assetid: 13cd5b1b-e906-4cd8-9b2b-510d587c665a
ms.openlocfilehash: da5fe354724427ae6806424122281d1653ebca22
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382982"
---
# <a name="compiler-error-c2725"></a>Compilerfehler C2725

'exception': Auslösen oder Erfassen eines verwalteten oder WinRT-Objekts nach Wert oder Verweis nicht möglich

Der Typ einer verwalteten oder WinRT-Ausnahme war falsch.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2725 generiert und gezeigt, wie Sie diesen Fehler beheben:

```
// C2725.cpp
// compile with: /clr
ref class R {
public:
   int i;
};

int main() {
   R % r1 = *gcnew R;
   throw r1;   // C2725

   R ^ r2 = gcnew R;
   throw r2;   // OK
}
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2725 generiert und gezeigt, wie Sie diesen Fehler beheben:

```
// C2725b.cpp
// compile with: /clr
using namespace System;
int main() {
   try {}
   catch( System::Exception%) {}   // C2725
   // try the following line instead
   // catch( System::Exception ^e) {}
}
```
