---
title: Compilerfehler C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: f643b7d8c035b4d1d7d8806feb5b121cf76d7796
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367576"
---
# <a name="compiler-error-c2698"></a>Compilerfehler C2698

Die using-Deklaration für "Deklaration 1" kann nicht gleichzeitig vorhanden sein, mit der vorhandenen using-Deklaration für "Deklaration 2"

Nachdem Sie haben eine [using-Deklaration](../../cpp/using-declaration.md) für einen Datenmember, die jede Deklaration im gleichen Bereich mit dem gleichen Namen ist nicht zulässig, da nur Funktionen, die überladen werden können.

Im folgende Beispiel wird die C2698 generiert:

```
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```