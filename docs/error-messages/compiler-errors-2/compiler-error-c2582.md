---
title: Compilerfehler C2582
ms.date: 11/04/2016
f1_keywords:
- C2582
helpviewer_keywords:
- C2582
ms.assetid: ee1b9378-8bcd-4792-b87e-6d7a466d29ed
ms.openlocfilehash: 2becaf3cf955a9ed8dbbc22cbf11728bcc5bec34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366731"
---
# <a name="compiler-error-c2582"></a>Compilerfehler C2582

' Funktion ' ist in "Type" nicht verfügbar

Es wurde versucht, ein Objekt zuweisen, die nicht über einen Zuweisungsoperator verfügt.

Im folgende Beispiel wird die C2582 generiert:

```
// C2582.cpp
// compile with: /clr
using namespace System;

struct N {};
ref struct O {};
ref struct R {
   property O prop;   // C2582
   property O ^ prop2;   // OK
};

int main() {
   String ^ st1 = gcnew String("");
   ^st1 = gcnew String("");   // C2582
   st1 = "xxx";   // OK
}
```