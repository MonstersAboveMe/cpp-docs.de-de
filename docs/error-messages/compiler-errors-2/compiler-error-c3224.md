---
title: Compilerfehler C3224
ms.date: 11/04/2016
f1_keywords:
- C3224
helpviewer_keywords:
- C3224
ms.assetid: 129be22f-8f3e-4fc6-9ccd-d27d8ef91251
ms.openlocfilehash: dc64ca1aeef66eeb554be1316bf9433145b50cc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174054"
---
# <a name="compiler-error-c3224"></a>Compilerfehler C3224

"Typ": Keine überladene generische Klasse übernimmt "Zahl" generische Typargumente.

Der Compiler konnte keine entsprechende Überladung finden.

Im folgenden Beispiel wird C3224 generiert:

```
// C3224.cs
// compile with: /target:library
public class C<T> {}
public class C<T,U> {}
```

und anschließend

```
// C3224b.cpp
// compile with: /clr
#using "C3224.dll"
int main() {
   C<int,int,int>^ c = gcnew C<int,int,int>();   // C3224
   C<int,int>^ c2 = gcnew C<int,int>();   // OK
}
```