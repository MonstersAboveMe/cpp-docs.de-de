---
title: Compilerwarnung (Stufe 1) C4486
ms.date: 11/04/2016
f1_keywords:
- C4486
helpviewer_keywords:
- C4486
ms.assetid: 2c0c59e3-d025-4d97-8da2-fa27df1402fc
ms.openlocfilehash: 402d5eefde6c2dfd5693e53c27edb00d1ac2e56c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404064"
---
# <a name="compiler-warning-level-1-c4486"></a>Compilerwarnung (Stufe 1) C4486

'Funktion': eine private virtuelle Methode einer Verweisklasse oder einer Werteklasse sollte "sealed" markiert werden

Da eine private virtuelle Memberfunktion einer verwalteten Klasse oder Struktur zugegriffen noch außer Kraft gesetzt werden, es sollte markiert werden [versiegelten](../../extensions/sealed-cpp-component-extensions.md).

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C4486 generiert.

```
// C4486.cpp
// compile with: /clr /c /W1
ref class B {
private:
   virtual void f() {}   // C4486
   virtual void f1() sealed {}   // OK
};
```

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine mögliche Verwendung der eine private versiegelt, virtuell-Funktion.

```
// C4486_b.cpp
// compile with: /clr /c
ref class B {};

ref class D : B {};

interface class I {
   B^ mf();
};

ref class E : I {
private:
   virtual B^ g() sealed = I::mf {
      return gcnew B;
   }

public:
   virtual D^ mf() {
      return gcnew D;
   }
};
```