---
title: Compilerfehler C3623
ms.date: 11/04/2016
f1_keywords:
- C3623
helpviewer_keywords:
- C3623
ms.assetid: a0341b45-062a-4f67-beb9-ba74201ed1ed
ms.openlocfilehash: dd12e64e775807220b4ece1f4c26a2f52437c69e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221904"
---
# <a name="compiler-error-c3623"></a>Compilerfehler C3623

„Variable“: Bitfelder werden in verwalteten oder WinRT-Typen nicht unterstützt.

Die Verwendung von Bitfeldern ist für Variablen in einer verwalteten oder WinRT-Klasse nicht zulässig.

Im folgenden Beispiel wird C3623 generiert:

```
// C3623.cpp
// compile with: /clr
using namespace System;
ref class CMyClass {
public:
   int i : 1;   // C3623
};

int main() {
   CMyClass^ pMyClass = gcnew CMyClass();
   pMyClass->i = 3;
   Console::Out->WriteLine(pMyClass->i);
}
```
