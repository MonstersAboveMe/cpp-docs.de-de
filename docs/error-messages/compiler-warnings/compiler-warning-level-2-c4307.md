---
title: Compilerwarnung (Stufe 2) C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: e9ad30f60260893130beed921aab811c894868cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402501"
---
# <a name="compiler-warning-level-2-c4307"></a>Compilerwarnung (Stufe 2) C4307

'Operator': Überlauf einer ganzzahligen Konstanten

Der Operator wird in einem Ausdruck verwendet, die eine ganzzahlige Konstante Überlauf für diese zugeordneten Speicherplatzes ergeben. Sie müssen möglicherweise einen größeren Typ für die Konstante verwenden. Ein **signiert Int** enthält einen kleineren Wert als ein `unsigned int` da die **signiert Int** ein Bit verwendet, um das Zeichen darzustellen.

Im folgende Beispiel wird die C4307 generiert:

```
// C4307.cpp
// compile with: /W2
int i = 2000000000 + 2000000000;   // C4307
int j = (unsigned)2000000000 + 2000000000;   // OK

int main()
{
}
```