---
title: Compilerfehler C2042
ms.date: 11/04/2016
f1_keywords:
- C2042
helpviewer_keywords:
- C2042
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
ms.openlocfilehash: 3302b3a529ad8af054bb29bced66bc939abcc060
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384438"
---
# <a name="compiler-error-c2042"></a>Compilerfehler C2042

Die Schlüsselwörter "signed/unsigned" schließen sich gegenseitig aus

Die Schlüsselwörter `signed` und `unsigned` werden innerhalb der gleichen Deklaration verwendet.

Im folgenden Beispiel wird C2042 generiert:

```
// C2042.cpp
unsigned signed int i;   // C2042
```

Mögliche Lösung:

```
// C2042b.cpp
// compile with: /c
unsigned int i;
signed int ii;
```