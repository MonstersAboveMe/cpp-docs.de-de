---
title: Compilerfehler C3351
ms.date: 11/04/2016
f1_keywords:
- C3351
helpviewer_keywords:
- C3351
ms.assetid: c021bbbe-1067-4f51-af4f-940d2b792eb5
ms.openlocfilehash: 3935acc645403efcd579a80340ebb9794bc1052a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402657"
---
# <a name="compiler-error-c3351"></a>Compilerfehler C3351

'Object': Delegatkonstruktor: Das zweite Argument muss eine Adresse einer statischen Memberfunktion oder einer globalen Funktion sein.

Der Compiler hat die Adresse einer Funktion erwartet, die als `static`deklariert ist.

Im folgenden Beispiel wird C3351 generiert:

```
// C3351a.cpp
// compile with: /clr
delegate int D(int, int);

ref class C {
public:
   int mf(int, int) {
      return 1;
   }

   static int mf2(int, int) {
      return 1;
   }
};

int main() {
   System::Delegate ^pD = gcnew D(nullptr, &C::mf);   // C3351
   System::Delegate ^pD2 = gcnew D(&C::mf2);
}
```
