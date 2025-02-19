---
title: Compilerwarnung (Stufe 1) C4002
ms.date: 11/04/2016
f1_keywords:
- C4002
helpviewer_keywords:
- C4002
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
ms.openlocfilehash: f2d2166a1370c02cfbc2346a63a424239ccb2b92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187260"
---
# <a name="compiler-warning-level-1-c4002"></a>Compilerwarnung (Stufe 1) C4002

Zu viele übergebene Parameter für das Makro "Bezeichner"

Die Anzahl der tatsächlich im Makro enthaltenen Parameter überschreitet die Anzahl der formalen Parameter in der Makrodefinition. Der Präprozessor erfasst die zusätzlichen Parameter, aber ignoriert diese bei der Makroerweiterung.

C4002 kann bei falscher Verwendung von [Variadic Macros](../../preprocessor/variadic-macros.md)auftreten.

Im folgenden Beispiel wird C4002 generiert:

```
// C4002.cpp
// compile with: /W1
#define test(a) (a)

int main() {
   int a = 1;
   int b = 2;
   a = test(a,b);   // C4002
   // try..
   a = test(a);
}
```

Dieser Fehler kann auch infolge einer Konformitätsverbesserung für Compiler für Visual Studio .NET 2003 auftreten: Zusätzliche Kommas in Makros werden nicht mehr akzeptiert.

Zusätzliche Kommas in Makros werden vom Compiler nicht mehr akzeptiert. Entfernen Sie zusätzliche Kommas, damit der Code in den Visual Studio .NET 2003- und Visual Studio .NET-Versionen von Visual C++ gültig ist.

```
// C4002b.cpp
// compile with: /W1
#define F(x,y)
int main()
{
   F(2,,,,,,3,,,,,,)   // C4002
   // Try the following line instead:
   // F(2,3)
}
```