---
title: Compilerfehler C2469
ms.date: 11/04/2016
f1_keywords:
- C2469
helpviewer_keywords:
- C2469
ms.assetid: 3814bdff-581a-4d3e-8b47-8de6887cea69
ms.openlocfilehash: e9c447451b052841da2ef0c7be582257ee216785
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303061"
---
# <a name="compiler-error-c2469"></a>Compilerfehler C2469

"Operator": "Typ"-Objekt kann nicht zugeordnet werden

Einem Operator wurde ein ungültiger Typ übergeben.

Im folgenden Beispiel wird C2469 generiert:

```
// C2469.cpp
int main() {
   int *i = new void;   // C2469
   int *i = new int;   // OK
}
```