---
title: Compilerfehler C3894
ms.date: 11/04/2016
f1_keywords:
- C3894
helpviewer_keywords:
- C3894
ms.assetid: 6d5ac903-1dea-431d-8e3a-cebca4342983
ms.openlocfilehash: 4d935e140d89cb5c3714450597677a7a02a245e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385484"
---
# <a name="compiler-error-c3894"></a>Compilerfehler C3894

'Var': l-Wert-Verwendung der statischen Initonly-Datenmembers ist nur zulässig, in den Konstruktor der Klasse der Klasse "Klasse"

Statische [Initonly](../../dotnet/initonly-cpp-cli.md) Datenmember können nur als l-Werte zum Zeitpunkt der Deklaration oder in einem statischen Konstruktor verwendet werden.

Instanz (nicht statisch) Initonly-Datenmember können nur als l-Werte zum Zeitpunkt der Deklaration oder in den Instanzkonstruktoren der (nicht statisch) verwendet werden.

Im folgende Beispiel wird die C3894 generiert:

```
// C3894.cpp
// compile with: /clr
ref struct Y1 {
   initonly static int data_var = 0;

public:
   // class constructor
   static Y1() {
      data_var = 99;   // OK
      System::Console::WriteLine("in static constructor");
   }

   // not the class constructor
   Y1(int i) {
      data_var = i;   // C3894
   }

   static void Test() {}

};

int main() {
   Y1::data_var = 88;   // C3894
   int i = Y1::data_var;
   Y1 ^ MyY1 = gcnew Y1(99);
   Y1::Test();
}
```