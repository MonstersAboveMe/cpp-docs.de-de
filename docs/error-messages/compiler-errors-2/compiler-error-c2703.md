---
title: Compilerfehler C2703
ms.date: 11/04/2016
f1_keywords:
- C2703
helpviewer_keywords:
- C2703
ms.assetid: 384295c3-643d-47ae-a9a6-865b3036aa84
ms.openlocfilehash: 363e3de497a7226a7c1dddd5769a047e6ea53e29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161393"
---
# <a name="compiler-error-c2703"></a>Compilerfehler C2703

Ungültige __leave-Anweisung

Ein `__leave` Anweisung muss innerhalb einer `__try` Block.

Im folgende Beispiel wird die C2703 generiert:

```
// C2703.cpp
int main() {
   __leave;   // C2703
   __try {
      // try the following line instead
      __leave;
   }
   __finally {}
}
```