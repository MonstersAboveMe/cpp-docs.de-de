---
title: Compilerfehler C2881
ms.date: 11/04/2016
f1_keywords:
- C2881
helpviewer_keywords:
- C2881
ms.assetid: b49c63c2-b064-4d4b-a75e-ddd2af947522
ms.openlocfilehash: 82a4fbe94bc7250244d57f549e52037d6a54c784
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378915"
---
# <a name="compiler-error-c2881"></a>Compilerfehler C2881

'namespace1': ist bereits als Alias für 'namespace2' verwendet

Sie können nicht den gleichen Namen als Alias für zwei Namespaces verwenden.

Im folgende Beispiel wird die C2881 generiert:

```
// C2881.cpp
// compile with: /c
namespace A {
   int k;
}

namespace B {
   int i;
}

namespace C = A;
namespace C = B;   // C2881 C is already an alias for A
```