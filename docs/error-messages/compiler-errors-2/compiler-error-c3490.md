---
title: Compilerfehler C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: 1e6c3c502290e88feec89877de7ad791084401cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381071"
---
# <a name="compiler-error-c3490"></a>Compilerfehler C3490

"var" kann nicht geändert werden, da über ein Konstantenobjekt darauf zugegriffen wird

Ein Lambda-Ausdruck, der in einer `const` -Methode deklariert ist, kann nicht änderbare Memberdaten nicht ändern.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Entfernen Sie den `const` -Modifizierer aus der Methodendeklaration.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3490 generiert, da die Membervariable `_i` in einer `const` -Methode geändert wird:

```
// C3490a.cpp
// compile with: /c

class C
{
   void f() const
   {
      auto x = [=]() { _i = 20; }; // C3490
   }

   int _i;
};
```

## <a name="example"></a>Beispiel

Im folgende Beispiel wird C3490 durch Entfernen des `const` -Modifizierers aus der Methodendeklaration aufgelöst:

```
// C3490b.cpp
// compile with: /c

class C
{
   void f()
   {
      auto x = [=]() { _i = 20; };
   }

   int _i;
};
```

## <a name="see-also"></a>Siehe auch

[Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md)