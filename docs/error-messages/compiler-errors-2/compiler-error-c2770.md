---
title: Compilerfehler C2770
ms.date: 11/04/2016
f1_keywords:
- C2770
helpviewer_keywords:
- C2770
ms.assetid: 100001b5-80b0-4971-8ff6-9023f443c926
ms.openlocfilehash: 9397b52838f61449f0475a31d5bb4077dad7f587
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257400"
---
# <a name="compiler-error-c2770"></a>Compilerfehler C2770

Ungültige explizite Template_or_generic-Argumente für "Template"

Funktionsvorlagen mit expliziten oder generischen Argumente führte zu unzulässigen Funktionstypen.

Im folgende Beispiel wird die C2770 generiert:

```
// C2770.cpp
#include <stdio.h>
template <class T>
int f(typename T::B*);   // expects type with member B

struct Err {};

int main() {
   f<int>(0);   // C2770 int has no B
   // try the following line instead
   f<OK>(0);
}
```