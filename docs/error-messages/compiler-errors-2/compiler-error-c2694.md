---
title: Compilerfehler C2694
ms.date: 11/04/2016
f1_keywords:
- C2694
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
ms.openlocfilehash: 4897512f6bd27465b7281d7a27757918128202d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367745"
---
# <a name="compiler-error-c2694"></a>Compilerfehler C2694

"override": überschreibende virtuelle Funktion hat weniger restriktive Ausnahmespezifikation als die Basisklasse virtueller Member-Funktion "Base"

Eine virtuelle Funktion überschrieben wurde, jedoch unter [/Za](../../build/reference/za-ze-disable-language-extensions.md), wird die Funktion überschreiben musste eine weniger restriktive [Ausnahmespezifikation](../../cpp/exception-specifications-throw-cpp.md).

Im folgende Beispiel wird die C2694 generiert:

```
// C2694.cpp
// compile with: /Za /c
class MyBase {
public:
   virtual void f(void) throw(int) {
   }
};

class Derived : public MyBase {
public:
   void f(void) throw(...) {}   // C2694
   void f2(void) throw(int) {}   // OK
};
```