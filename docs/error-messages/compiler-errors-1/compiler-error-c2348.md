---
title: Compilerfehler C2348
ms.date: 11/04/2016
f1_keywords:
- C2348
helpviewer_keywords:
- C2348
ms.assetid: 4c4d701f-ccf1-46fe-9ddb-3f341684f269
ms.openlocfilehash: 379bcc7f37ff8942e4e45c6a6188438400937875
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187905"
---
# <a name="compiler-error-c2348"></a>Compilerfehler C2348

"Typname": ist kein Aggregat im C-Stil, kann nicht in eingebetteter IDL exportiert werden

Platziert ein `struct` in einer IDL-Datei mit der [exportieren](../../windows/export.md) -Attribut, das `struct` muss nur Daten enthalten.

Im folgende Beispiel wird die C2348 generiert:

```
// C2348.cpp
// C2348 error expected
[ module(name="SimpleMidlTest") ];

[export]
struct Point {
   // Delete the following two lines to resolve.
   Point() : m_i(0), m_j(0) {}
   Point(int i, int j) : m_i(i), m_j(j) {}

   int m_i;
   int m_j;
};
```