---
title: Compilerwarnung (Stufe 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 28b3e49717993a3bf20c8cfec5938d698266c0f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406534"
---
# <a name="compiler-warning-level-1-c4804"></a>Compilerwarnung (Stufe 1) C4804

'Operation': unsichere Verwendung des Typs "Bool", Vorgang

Diese Warnung gilt für bei der Verwendung einer `bool` Variable oder ein Wert in der erwarteten Weise. C4804 wird beispielsweise generiert, bei der Verwendung Operatoren wie z. B. den negativen unäroperator (**-**) oder dem Komplementoperator (`~`). Der Compiler wertet den Ausdruck.

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C4804 generiert:

```
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```