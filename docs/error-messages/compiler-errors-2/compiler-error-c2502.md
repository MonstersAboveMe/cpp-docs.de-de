---
title: Compilerfehler C2502
ms.date: 11/04/2016
f1_keywords:
- C2502
helpviewer_keywords:
- C2502
ms.assetid: affa0b86-15fc-4e17-b7f2-6aad4a3771c4
ms.openlocfilehash: e23ccae55c40c9652f5a3e1f55c834a968bca784
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165579"
---
# <a name="compiler-error-c2502"></a>Compilerfehler C2502

'Bezeichner': zu viele Zugriffsmodifizierer für Basisklasse

Die Basisklasse verfügt über mehr als eine Zugriffsmodifizierer. Nur ein Zugriffsmodifizierer (`public`, `private`, oder `protected`) ist zulässig.

Im folgende Beispiel wird die C2502 generiert:

```
// C2502.cpp
// compile with: /c
class A { };
class B { };
class C : private public A { };   // C2502

// OK
class D : private A {};
class E : public A, private B {};
```