---
title: Compilerfehler C3269
ms.date: 11/04/2016
f1_keywords:
- C3269
helpviewer_keywords:
- C3269
ms.assetid: c575f067-244d-4dd5-bf58-9e7630ea58b7
ms.openlocfilehash: 406b388460b3d449471c884dd6461f2ce59a10f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365714"
---
# <a name="compiler-error-c3269"></a>Compilerfehler C3269

'Funktion': eine Memberfunktion einer verwalteten oder WinRTtype kann nicht mit '...' deklariert werden

Verwaltete und WinRT-Klassenmemberfunktionen können keine Parameterlisten variabler Länge deklarieren.

Im folgenden Beispiel wird C3269 generiert und gezeigt, wie Sie diesen Fehler beheben:

```
// C3269_2.cpp
// compile with: /clr

ref struct A
{
   void func(int i, ...)   // C3269
   // try the following line instead
   // void func(int i )
   {
   }
};

int main()
{
}
```
