---
title: Compilerfehler C2201
ms.date: 11/04/2016
f1_keywords:
- C2201
helpviewer_keywords:
- C2201
ms.assetid: ed927659-6e9c-447d-9963-19969ae1e957
ms.openlocfilehash: b490bc32a9da0a35a726371e3b17480fcd8b0df2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368603"
---
# <a name="compiler-error-c2201"></a>Compilerfehler C2201

'Bezeichner': externen Bindung um Export/Import benötigen.

Der exportierte Bezeichner hat `static`.

Im folgenden Beispiel wird C2286 generiert:

```
// C2201.cpp
// compile with: /c
__declspec(dllexport) static void func() {}   // C2201 func() is static
__declspec(dllexport) void func2() {}   // OK
```

## <a name="see-also"></a>Siehe auch

[Verknüpfungstypen](../../cpp/types-of-linkage.md)