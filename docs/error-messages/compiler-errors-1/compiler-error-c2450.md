---
title: Compilerfehler C2450
ms.date: 11/04/2016
f1_keywords:
- C2450
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
ms.openlocfilehash: 3cbab274f8f7cd04d5fb86db69572e0b7fc1c04e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208970"
---
# <a name="compiler-error-c2450"></a>Compilerfehler C2450

Switch-Ausdruck vom Typ 'Typ' ist nicht zulässig

Die `switch` Ausdruck ausgewertet wird, auf einen ungültigen Typ. Es muss ausgewertet werden, ein ganzzahliger Typ oder ein Klassentyp mit eindeutige Konvertierung in einen Integer-Datentyp. Wenn er auf einen benutzerdefinierten Typ ausgewertet wird, müssen Sie einen Konvertierungsoperator angeben.

Im folgende Beispiel wird die C2450 generiert:

```
// C2450.cpp
class X {
public:
   int i;
} x;

class Y {
public:
   int i;
   operator int() { return i; }   // conversion operator
} y;

int main() {
   int j = 1;
   switch ( x ) {   // C2450, x is not type int
   // try the following line instead
   // switch ( y ) {
      default:  ;
   }
}
```