---
title: Compilerfehler C2581
ms.date: 11/04/2016
f1_keywords:
- C2581
helpviewer_keywords:
- C2581
ms.assetid: 24a4e4c1-24d3-4e42-b760-7dcaf9740b16
ms.openlocfilehash: edfab092c82f9dc1d4b9dfe5d21daa2b2ab98d08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385861"
---
# <a name="compiler-error-c2581"></a>Compilerfehler C2581

"Type": statischer "Operator ="-Funktion ist nicht zulässig

Die Zuweisung (`=`)-Operator wurde falsch deklariert. als `static`. Zuweisungsoperatoren nicht `static`. Weitere Informationen finden Sie unter [User-Defined Operators (C++ / CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C2581 generiert.

```
// C2581.cpp
// compile with: /clr /c
ref struct Y {
   static Y ^ operator = (Y^ me, int i);   // C2581
   Y^ operator =(int i);   // OK
};
```