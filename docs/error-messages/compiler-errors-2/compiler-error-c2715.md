---
title: Compilerfehler C2715
ms.date: 11/04/2016
f1_keywords:
- C2715
helpviewer_keywords:
- C2715
ms.assetid: c81567a7-5b65-468f-aaf9-835f91e468e4
ms.openlocfilehash: 0f0df136952e09d26fbf43104bbf13b001c87255
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386758"
---
# <a name="compiler-error-c2715"></a>Compilerfehler C2715

'Typ': auslösen oder erfassen dieses Typs nicht möglich

Werttypen sind keine gültigen Argumente, mit der Behandlung von Ausnahmen in verwaltetem Code (siehe [Exception Handling](../../extensions/exception-handling-cpp-component-extensions.md) für Weitere Informationen).

```
// C2715a.cpp
// compile with: /clr
using namespace System;

value struct V {
   int i;
};

void f1() {
   V v;
   v.i = 10;
   throw v;   // C2715
   // try the following line instead
   // throw ((V^)v);
}

int main() {
   try {
      f1();
   }

   catch(V v) { if ( v.i == 10 ) {   // C2715
   // try the following line instead
   // catch(V^ pv) { if ( pv->i == 10 ) {
         Console::WriteLine("caught 10 - looks OK");
      }
      else {
         Console::WriteLine("catch looks bad");
      }
   }
   catch(...) {
      Console::WriteLine("catch looks REALLY bad");
   }
}
```
