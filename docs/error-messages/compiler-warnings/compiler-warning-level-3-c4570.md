---
title: Compilerwarnung (Stufe 3) C4570
ms.date: 11/04/2016
f1_keywords:
- C4570
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
ms.openlocfilehash: 386d7c210c77469d67a75d66f7d8ae35c105b3b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401786"
---
# <a name="compiler-warning-level-3-c4570"></a>Compilerwarnung (Stufe 3) C4570

'Typ': ist nicht explizit als abstrakte jedoch abstrakte Funktionen weist deklariert

Ein Typ, der enthält [abstrakte](../../extensions/abstract-cpp-component-extensions.md) Funktionen sollten sich selbst als abstrakt gekennzeichnet werden.

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C4570 generiert.

```
// C4570.cpp
// compile with: /clr /W3 /c
ref struct X {   // C4570
// try the following line instead
// ref class X abstract {
   virtual void f() abstract;
};
```