---
title: Compilerfehler C2563
ms.date: 11/04/2016
f1_keywords:
- C2563
helpviewer_keywords:
- C2563
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
ms.openlocfilehash: 04a10c82fa6aa39bcf1098d6d4aabfc2f769e7c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257854"
---
# <a name="compiler-error-c2563"></a>Compilerfehler C2563

nicht übereinstimmende in der Liste formaler parameter

Die Liste der formalen Parameter einer Funktion (oder ein Zeiger auf eine Funktion) entspricht nicht den von einer anderen Funktion (oder Zeiger auf eine Memberfunktion). Daher kann die Zuweisung von Funktionen oder Zeiger vorgenommen werden.

Im folgende Beispiel wird die C2563 generiert:

```
// C2563.cpp
void func( int );
void func( int, int );
int main() {
   void *fp();
   fp = func;   // C2563
}
```