---
title: Compilerfehler C2279
ms.date: 11/04/2016
f1_keywords:
- C2279
helpviewer_keywords:
- C2279
ms.assetid: 1b5c88ef-2336-49b8-9ddb-d61f97c73e14
ms.openlocfilehash: f35e384a5b242eb28427e1ff62ac55a3e9b206c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388862"
---
# <a name="compiler-error-c2279"></a>Compilerfehler C2279

Ausnahmespezifikation kann nicht in einer typedef-Deklaration angezeigt werden.

Klicken Sie unter **/Za**, [Ausnahmespezifikationen](../../cpp/exception-specifications-throw-cpp.md) sind in einer typedef-Deklaration nicht zulässig.

Im folgende Beispiel wird die C2279 generiert:

```
// C2279.cpp
// compile with: /Za /c
typedef int (*xy)() throw(...);   // C2279
typedef int (*xyz)();   // OK
```