---
title: Compilerwarnung (Stufe 1) C4550
ms.date: 11/04/2016
f1_keywords:
- C4550
helpviewer_keywords:
- C4550
ms.assetid: f902b4ed-5f17-48ea-b693-92f4fb8c8054
ms.openlocfilehash: eff3548ef43075a86f52086caf9b79158ad70cb9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410381"
---
# <a name="compiler-warning-level-1-c4550"></a>Compilerwarnung (Stufe 1) C4550

Ausdruck ausgewertet wird, um eine Funktion, die eine Argumentliste fehlt

Ein dereferenzierter Zeiger auf eine Funktion ist eine Argumentliste fehlt.

## <a name="example"></a>Beispiel

```
// C4550.cpp
// compile with: /W1
bool f()
{
   return true;
}

typedef bool (*pf_t)();

int main()
{
   pf_t pf = f;
   if (*pf) {}  // C4550
   return 0;
}
```