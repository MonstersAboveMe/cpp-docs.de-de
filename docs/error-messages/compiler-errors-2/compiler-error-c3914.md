---
title: Compilerfehler C3914
ms.date: 11/04/2016
f1_keywords:
- C3914
helpviewer_keywords:
- C3914
ms.assetid: 8f3190e6-ee50-4916-9ecc-3b8748b2e1e7
ms.openlocfilehash: e7c04da2b7574d3af0e1c05ae4adc3ad513faa0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406612"
---
# <a name="compiler-error-c3914"></a>Compilerfehler C3914

eine Standardeigenschaft kann nicht statisch sein.

Eine Default-Eigenschaft wurde falsch deklariert.  Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden Sie Eigenschaften in C++/CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3914 generiert und gezeigt, wie Sie diesen Fehler beheben.

```
// C3914.cpp
// compile with: /clr /c
ref struct X {
   static property int default[int] {   // C3914
   // try the following line instead
   // property int default[int] {
      int get(int) { return 0; }
      void set(int, int) {}
   }
};
```