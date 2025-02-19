---
title: Compilerwarnung (Stufe 1) C4965
ms.date: 11/04/2016
f1_keywords:
- C4965
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
ms.openlocfilehash: 2e93fdeba7f9b5b10340ccd1920807a3fcb345a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383839"
---
# <a name="compiler-warning-level-1-c4965"></a>Compilerwarnung (Stufe 1) C4965

Implizites Boxing mit ganzer Zahl 0.; Verwenden Sie "nullptr" oder eine explizite Umwandlung

Visual C++ verfügt über implizites Boxing von Werttypen. Eine Anweisung, die einen null-Zuweisung mit Managed Extensions for C++ jetzt geführt haben, wird eine Zuweisung zu einer geschachtelten "int".

Weitere Informationen finden Sie unter [Boxing](../../extensions/boxing-cpp-component-extensions.md)definiert sind.

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C4965 generiert.

```
// C4965.cpp
// compile with: /clr /W1
int main() {
   System::Object ^o = 0;   // C4965

   // the previous line is the same as the following line
   // using Managed Extensions for C++
   // System::Object *o = __box(0);

   // OK
   System::Object ^o2 = nullptr;
   System::Object ^o3 = safe_cast<System::Object^>(0);
}
```