---
title: Compilerwarnung (Stufe 1) C4114
ms.date: 11/04/2016
f1_keywords:
- C4114
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
ms.openlocfilehash: 41e951e7c4a8b23ddbec14c5421f66702e70c937
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300257"
---
# <a name="compiler-warning-level-1-c4114"></a>Compilerwarnung (Stufe 1) C4114

Der gleiche Typqualifizierer wurde mehrmals verwendet

Eine Typdeklaration oder-Definition verwendet ein Typqualifizierer (**const**, **flüchtige**, **signiert**, oder **ohne Vorzeichen**) mehr als einmal. Dies bewirkt, dass eine Warnung mit Microsoft-Erweiterungen (/ Ze) und ANSI-Kompatibilität (/ Za).

Im folgende Beispiel wird die C4114 generiert:

```
// C4114.cpp
// compile with: /W1 /c
volatile volatile int i;   // C4114
```

Im folgende Beispiel wird die C4114 generiert:

```
// C4114_b.cpp
// compile with: /W1 /c
static const int const * ii;   // C4114
static const int * const iii;   // OK
```
