---
title: Compilerfehler C2293
ms.date: 11/04/2016
f1_keywords:
- C2293
helpviewer_keywords:
- C2293
ms.assetid: 17e7b4e2-368b-4dd7-a01b-d82be60f8e56
ms.openlocfilehash: 8073e952e8248367c444415cfb182743247dc6fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182742"
---
# <a name="compiler-error-c2293"></a>Compilerfehler C2293

"Bezeichner": Eine Member-Variable kann nicht als __based-Spezifizierer verwendet werden

Spezifizierer für einen `__based` -Modifizierer müssen Nichtmember-Zeiger sein.

Das folgende Beispiel generiert C2293:

```
// C2293.cpp
// compile with: /c
class A {
   static int *i;
   void __based(i) *bp;   // C2293
   void *bp2;   // OK
};
```