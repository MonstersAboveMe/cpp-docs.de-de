---
title: Compilerfehler C3697
ms.date: 11/04/2016
f1_keywords:
- C3697
helpviewer_keywords:
- C3697
ms.assetid: 2d3f63c4-b7f8-421d-a7a5-2bf17fd054f9
ms.openlocfilehash: 55eadd55af8d4e6f088a0d0eb732d820242cae66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363686"
---
# <a name="compiler-error-c3697"></a>Compilerfehler C3697

'Qualifizierer": dieser Qualifizierer kann bei nicht verwendet ' ^'

Die Trackinghandle (^) wurde auf einen Qualifizierer angewendet, für das sie nicht entwickelt wurde.

Im folgende Beispiel wird die C3697 generiert:

```
// C3697.cpp
// compile with: /clr
using namespace System;
int main() {
   String ^__restrict s;   // C3697
   String ^ s2;   // OK
}
```