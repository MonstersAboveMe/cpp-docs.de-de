---
title: Compilerfehler C3753
ms.date: 11/04/2016
f1_keywords:
- C3753
helpviewer_keywords:
- C3753
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
ms.openlocfilehash: 7c9c078e72babc85dc7092b8d6414625e9c0db7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410472"
---
# <a name="compiler-error-c3753"></a>Compilerfehler C3753

eine generische Eigenschaft ist nicht zulässig.

Generische Parameterlisten können nur für verwaltete Klassen, Strukturen oder Funktionen angezeigt werden.

Weitere Informationen finden Sie unter [Generika](../../extensions/generics-cpp-component-extensions.md) und [Eigenschaft](../../extensions/property-cpp-component-extensions.md).

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C3753 generiert.

```
// C3753.cpp
// compile with: /clr /c
ref struct A {
   generic <typename T>
   property int i;   // C3753 error
};
```