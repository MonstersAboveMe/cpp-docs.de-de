---
title: Compilerfehler C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: 44f7988f9fedb882972b2823f2fe70d9512d4e87
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408679"
---
# <a name="compiler-error-c2801"></a>Compilerfehler C2801

'Operator Operator' muss einen nicht statischen Member sein.

Die folgenden Operatoren können überladen werden, nur als nicht statische Member:

- Zuweisung `=`

- Klassenmemberzugriff `->`

- Indizierung `[]`

- Funktionsaufruf `()`

Mögliche Ursachen für C2801:

- Überladener Operator ist nicht an eine Klasse, Struktur oder union-Member.

- Überladener Operator deklariert `static`.

- Im folgende Beispiel wird die C2801 generiert:

```
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```