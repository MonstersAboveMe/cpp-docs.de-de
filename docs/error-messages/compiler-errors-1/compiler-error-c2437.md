---
title: Compilerfehler C2437
ms.date: 11/04/2016
f1_keywords:
- C2437
helpviewer_keywords:
- C2437
ms.assetid: 2d2b3c6c-856a-4b27-ae10-64813b3e5483
ms.openlocfilehash: 93b642d9bfbb5a8d938e3dfba6e3ad5fe8b3cbb0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375079"
---
# <a name="compiler-error-c2437"></a>Compilerfehler C2437

'Bezeichner': bereits initialisiert.

Ein Objekt kann nur einmal initialisiert werden.

Im folgende Beispiel wird die C2437 generiert:

```
// C2437.cpp
// compile with: /c
class A {
public:
   A(int i) {}
};

class B : A {
   B() : A(1), A(2) {}   // C2437
   B() : A(1) {}   // OK
};
```