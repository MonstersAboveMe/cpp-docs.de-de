---
title: Compilerfehler C3923
ms.date: 11/04/2016
f1_keywords:
- C3923
helpviewer_keywords:
- C3923
ms.assetid: db8838e9-6344-4cd6-83e0-a8abeb12c4c0
ms.openlocfilehash: 82bdfef997248dea11784c00fc04d1ac3b4189d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386563"
---
# <a name="compiler-error-c3923"></a>Compilerfehler C3923

„member“: Definitionen für lokale Klassen, Strukturen oder Unions sind in einer Memberfunktion einer verwalteten oder WinRT-Klasse nicht zulässig.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3923 generiert.

```
// C3923.cpp
// compile with: /clr /c
ref struct x {
   void Test() {
      struct a {};   // C3923
      class b {};   // C3923
      union c {};   // C3923
   }
};
```