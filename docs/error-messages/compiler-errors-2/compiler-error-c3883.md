---
title: Compilerfehler C3883
ms.date: 11/04/2016
f1_keywords:
- C3883
helpviewer_keywords:
- C3883
ms.assetid: cdd1c1f4-f268-4469-9c62-d52303114b0c
ms.openlocfilehash: 51ecf5fbc793c02a23e2aa02fb08e37ebe4b0ad0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347037"
---
# <a name="compiler-error-c3883"></a>Compilerfehler C3883

"Var": ein statischer Initonly-Datenmember muss initialisiert werden

Eine Variable, die mit markierten [Initonly](../../dotnet/initonly-cpp-cli.md) wurde nicht ordnungsgemäß initialisiert.

Im folgende Beispiel wird die C3883 generiert:

```
// C3883.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   static int staticConst1;   // C3883
};
```

Das folgende Beispiel zeigt eine mögliche Lösung:

```
// C3883b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int staticConst2 = 0;
};
```

Im folgende Beispiel wird veranschaulicht, wie in einem statischen Konstruktor initialisiert werden:

```
// C3883c.cpp
// compile with: /clr /LD
ref struct Y1 {
   initonly
   static int staticConst1;

   static Y1() {
      staticConst1 = 0;
   }
};
```