---
title: Compilerfehler C2550
ms.date: 11/04/2016
f1_keywords:
- C2550
helpviewer_keywords:
- C2550
ms.assetid: 3293f53e-ee66-4035-920d-34e115c3a24c
ms.openlocfilehash: 2df6ae70be31bc519e6cfd826646073becf1ad61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353351"
---
# <a name="compiler-error-c2550"></a>Compilerfehler C2550

"Bezeichner": Initialisierungslisten für Konstruktoren dürfen nur in Konstruktordefinition stehen

Eine Initialisiererliste Basisklasse wird auf die Definition einer Funktion verwendet, die kein Konstruktor ist.

Im folgende Beispiel wird die C2550 generiert:

```
// C2550.cpp
// compile with: /c
class C {
public:
   C();
};

class D : public C {
public:
   D();
   void func();
};

void D::func() : C() {}  // C2550
D::D() : C() {}   // OK
```