---
title: Compilerfehler C3239
ms.date: 11/04/2016
f1_keywords:
- C3239
helpviewer_keywords:
- C3239
ms.assetid: 22a518b7-020f-4f3c-9963-a094667fd1ac
ms.openlocfilehash: ec5a1e3a968c9342ba6d386ef1e2be133e45b62c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174041"
---
# <a name="compiler-error-c3239"></a>Compilerfehler C3239

'Typ': Zeiger auf inneren/festen Zeiger ist gemäß Common Language Runtime nicht zulässig.

Der Compiler hat einen ungültigen Typ festgestellt.

Im folgenden Beispiel wird C3229 generiert:

```
// C3239.cpp
// compile with: /clr
int main() {
   interior_ptr<int>* pip0;   // C3239

   // OK
   int * pip1;
   interior_ptr<int> pip2;
   int ** pip;
}
```