---
title: Compilerfehler C3277
ms.date: 11/04/2016
f1_keywords:
- C3277
helpviewer_keywords:
- C3277
ms.assetid: 8ac5f476-e30c-4879-92c6-f03cdbd74045
ms.openlocfilehash: e49de69354d00babf8c6fa609e92153e88bf64c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382111"
---
# <a name="compiler-error-c3277"></a>Compilerfehler C3277

eine nicht verwaltete Enumeration 'Enumeration' kann nicht innerhalb der verwalteten 'Typs' definiert werden.

Eine Enumeration wurde nicht ordnungsgemäß innerhalb eines verwalteten Typs definiert.

Im folgende Beispiel wird die C3277 generiert:

```
// C3277a.cpp
// compile with: /clr
ref class A
{
   enum E {e1,e2};   // C3277
   // try the following line instead
   // enum class E {e1,e2};
};

int main()
{
}
```
