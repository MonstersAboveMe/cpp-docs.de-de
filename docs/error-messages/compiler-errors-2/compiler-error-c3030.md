---
title: Compilerfehler C3030
ms.date: 11/04/2016
f1_keywords:
- C3030
helpviewer_keywords:
- C3030
ms.assetid: de92fd7e-29ba-46e8-b43b-f4b985cd74de
ms.openlocfilehash: 31ae3f55cd0bf7a15dbea2cf941b00dc048d825d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375534"
---
# <a name="compiler-error-c3030"></a>Compilerfehler C3030

'var': Die Variable in der reduction-Klausel/-Direktive kann keinen Verweistyp aufweisen

Bestimmten Klauseln, wie etwa der reduction-Klausel, können nur Wertparameter übergeben werden.

Im folgenden Beispiel wird C3030 generiert:

```
// C3030.cpp
// compile with: /openmp /link vcomps.lib
#include "omp.h"

void test(int &r) {
   #pragma omp parallel reduction(+ : r)   // C3030
      ;
}

void test2(int r) {
   #pragma omp parallel reduction(+ : r)   // OK
      ;
}

int main(int argc, char** argv) {
   int& r = *((int*)argv);
   int s = *((int*)argv);

   #pragma omp parallel reduction(+ : r)   // C3030
      ;

   #pragma omp parallel reduction(+ : s)   // OK
      ;
}
```