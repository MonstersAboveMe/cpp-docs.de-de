---
title: Compilerfehler C2635
ms.date: 11/04/2016
f1_keywords:
- C2635
helpviewer_keywords:
- C2635
ms.assetid: 9deca2a8-2d61-42eb-9783-6578132ee3fb
ms.openlocfilehash: 0c31bcc4062aec1d939c801f9b5ee420f2f4fcb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367849"
---
# <a name="compiler-error-c2635"></a>Compilerfehler C2635

Konvertierung einer 'Bezeichner1*"in einer" Bezeichner2\*"; Konvertierung von einer virtuellen Basisklasse wird impliziert.

Die Konvertierung erforderlich ist, eine Umwandlung aus einer `virtual` Basisklasse auf eine abgeleitete Klasse, die unzulässig ist.

Im folgende Beispiel wird die C2635 generiert:

```
// C2635.cpp
class B {};
class D : virtual public B {};
class E : public B {};

int main() {
   B b;
   D d;
   E e;

   D * pD = &d;
   E * pE = &e;
   pD = (D*)&b;   // C2635
   pE = (E*)&b;   // OK
}
```