---
title: Compilerfehler C2658
ms.date: 11/04/2016
f1_keywords:
- C2658
helpviewer_keywords:
- C2658
ms.assetid: 638368e8-7893-4a14-abec-13c768a9543a
ms.openlocfilehash: 792fd497ad7cdb98ae72f3e6451780dad487624d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360410"
---
# <a name="compiler-error-c2658"></a>Compilerfehler C2658

'Member': Neudefinition in anonymes Struct/Union

Zwei anonyme Strukturen oder Unions enthalten Memberdeklarationen mit dem gleichen Bezeichner jedoch mit unterschiedlichen Typen auf. Klicken Sie unter [/Za](../../build/reference/za-ze-disable-language-extensions.md), erhalten Sie auch diese Fehlermeldung für Elemente mit dem gleichen Bezeichner und dem angegebenen Typ.

Im folgende Beispiel wird die C2658 generiert:

```
// C2658.cpp
// compile with: /c
struct X {
   union { // can be struct too
      int i;
   };
   union {
      int i;   // Under /Za, C2658
      // int i not needed here because it is defined in the first union
   };
};

struct Z {
   union {
      char *i;
   };

   union {
      void *i;   // C2658 redefinition of 'i'
      // try the following line instead
      // void *ii;
   };
};
```