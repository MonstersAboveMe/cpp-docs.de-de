---
title: Compilerfehler C3395
ms.date: 11/04/2016
f1_keywords:
- C3395
helpviewer_keywords:
- C3395
ms.assetid: 26a9ebc9-ed97-47ce-b436-19aa2bcf6e50
ms.openlocfilehash: 2e5234abcbe46e17035fd0b16e9816c879d86cfe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243049"
---
# <a name="compiler-error-c3395"></a>Compilerfehler C3395

"Function": __declspec(dllexport) kann nicht angewendet werden, um eine Funktion mit dem \__clrcall-Aufrufkonvention

`__declspec(dllexport)` und [__clrcall](../../cpp/clrcall.md) sind nicht kompatibel.  Weitere Informationen finden Sie unter [Dllexport, Dllimport](../../cpp/dllexport-dllimport.md).

Im folgende Beispiel wird die C3395 generiert:

```
// C3395.cpp
// compile with: /clr /c

__declspec(dllexport) void __clrcall Test(){}   // C3395
void __clrcall Test2(){}   // OK
__declspec(dllexport) void Test3(){}   // OK
```