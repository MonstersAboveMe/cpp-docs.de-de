---
title: Compilerfehler C3014
ms.date: 11/04/2016
f1_keywords:
- C3014
helpviewer_keywords:
- C3014
ms.assetid: af1c5b0c-dbf9-4274-b06a-c6c2cdcf2a52
ms.openlocfilehash: c87c63641fc8071f7a1f29874ae7ae6dbffd4f70
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344672"
---
# <a name="compiler-error-c3014"></a>Compilerfehler C3014

Es wurde erwartet, dass auf die Direktive 'direktive' von OpenMP eine For-Schleife folgt.

Direktes Folgen auf eine `for` -Direktive stellt für alles, was keine `#pragma omp for` -Schleife ist, einen Fehler dar.

Im folgenden Beispiel wird C3014 generiert:

```
// C3014.cpp
// compile with: /openmp
int main()
{
   int i = 0;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 10; ++i)   // OK
      {
      }
   }

   #pragma omp parallel for
   for (i = 0; i < 10; ++i)   // OK
   {
   }

   #pragma omp parallel
   {
      #pragma omp for
      {   // C3014
         for (i = 0; i < 10; ++i)
         {
         }
      }
   }

   #pragma omp parallel for
   {   // C3014
      for (i = 0; i < 10; ++i)
      {
      }
   }

   #pragma omp parallel
   {
      #pragma omp for
      i *= 2;   // C3014
      for (i = 0; i < 10; ++i)
      {
      }
   }

   #pragma omp parallel for
   i *= 2;   // C3014
   for (i = 0; i < 10; ++i)
   {
   }
}
```