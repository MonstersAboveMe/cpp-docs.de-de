---
title: Compilerfehler C2276
ms.date: 11/04/2016
f1_keywords:
- C2276
helpviewer_keywords:
- C2276
ms.assetid: 62005ad9-6cb9-4b1f-965d-b875adaf695e
ms.openlocfilehash: 2128be2be4f0b5be37bbfc5098a35bb39afe5906
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388838"
---
# <a name="compiler-error-c2276"></a>Compilerfehler C2276

'Operator': Ungültige Operation auf Ausdruck einer gebundenen Memberfunktion

Der Compiler hat ein Problem mit der Syntax zum Erstellen einer Pointer-to-Member gefunden.

Im folgende Beispiel wird die C2276 generiert:

```
// C2276.cpp
class A {
public:
   int func(){return 0;}
} a;

int (*pf)() = &a.func;   // C2276
// try the following line instead
// int (A::*pf3)() = &A::func;

class B {
public:
   void mf() {
      &this -> mf;   // C2276
      // try the following line instead
      // &B::mf;
   }
};

int main() {
   A a;
   &a.func;   // C2276
   // try the following line instead
   // &A::func;
}
```