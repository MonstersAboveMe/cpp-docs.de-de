---
title: Compilerfehler C3017
ms.date: 11/04/2016
f1_keywords:
- C3017
helpviewer_keywords:
- C3017
ms.assetid: 12ab2c2a-d0d2-4900-9cbf-39be0af590dd
ms.openlocfilehash: 7172d870c509e79bf0900604302c38bc6ca9cd77
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360345"
---
# <a name="compiler-error-c3017"></a>Compilerfehler C3017

Der Beendigungstest in der For-Anweisung von OpenMP weist eine ungültige Form auf.

Eine `for` -Schleife in einer OpenMP-Anweisung muss vollständig und explizit angegeben werden.

Im folgenden Beispiel wird C3017 generiert.

```
// C3017.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i; ++i)   // C3017
      // Try the following line instead:
      // for (i = 0; i < 10; ++i)
         ;
   }
}
```