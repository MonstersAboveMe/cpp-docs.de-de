---
title: Compilerfehler C3854
ms.date: 11/04/2016
f1_keywords:
- C3854
helpviewer_keywords:
- C3854
ms.assetid: 32a9ead0-c6c7-485a-8802-c7b1fe921d3a
ms.openlocfilehash: 3b48e2c65003537102864fdafe7db70b06ade029
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265528"
---
# <a name="compiler-error-c3854"></a>Compilerfehler C3854

Ausdruck links von '=' wird als Funktion ausgewertet. Eine Funktion kann nicht zugewiesen (eine Funktion ist kein l-Wert)

Ein Verweis kann nicht erneut initialisiert werden. Dereferenzieren eines Verweises auf eine Funktion führt eine Funktion, die ein Rvalue-Wert, wird auf die Sie zuweisen können. Aus diesem Grund nicht über einen Verweis auf eine Funktion zugewiesen.

Im folgende Beispiel wird die C3854 generiert:

```
// C3854.cpp
int afunc(int i)
{
   return i;
}

typedef int (& rFunc_t)(int);
typedef int (* pFunc_t)(int);

int main()
{
   rFunc_t rf = afunc;   // OK binding a reference to function
   pFunc_t pf = &afunc;   // OK initializing a pointer to function

   *pf = &afunc;   // C3854
   // try the following line instead
   // pf = &afunc;
   *rf = &afunc;   // C3854
}
```