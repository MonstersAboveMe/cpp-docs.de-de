---
title: Compilerfehler C2227
ms.date: 11/04/2016
f1_keywords:
- C2227
helpviewer_keywords:
- C2227
ms.assetid: d470e8b8-7e15-468b-84fa-37d1a0132271
ms.openlocfilehash: 8f9fc435682eb400574eea61a6f90392fa679233
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404324"
---
# <a name="compiler-error-c2227"></a>Compilerfehler C2227

Links von „->member“ muss sich ein Zeiger auf Klassen-/Struktur-/Union-/generischen Typ befinden.

Der Operand auf der linken Seite des `->` ist kein Zeiger auf eine Klasse, Struktur oder Union.

Das folgende Beispiel generiert C2227:

```
// C2227.cpp
int *pInt;
struct S {
public:
    int member;
} s, *pS = &s;

int main() {
   pInt->member = 0;   // C2227 pInt points to an int
   pS->member = 0;   // OK
}
```