---
title: Compilerwarnung (Stufe 1) C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: b47d0bfbb6eab24fbe811d3e4f79b6bd86b3bb11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406469"
---
# <a name="compiler-warning-level-1-c4090"></a>Compilerwarnung (Stufe 1) C4090

'Operation': unterschiedliche 'Modifizierer'-Qualifizierer

Mit einem angegebenen Modifizierer, die verhindert, dass es unbemerkt vom Compiler geändert wird, wird eine Variable in einem Vorgang definiert. Der Ausdruck wird ohne Änderungen kompiliert.

Diese Warnung kann verursacht werden, wenn ein Zeiger auf eine **const** oder `volatile` Arbeitselement zugewiesen wird, auf einen Zeiger, der nicht deklariert, wie das Verweisen auf **const** oder `volatile`.

Diese Warnung wird für die C-Programmen ausgegeben. In einem C++ -Programm ist, gibt der Compiler einen Fehler: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).

Im folgende Beispiel wird die C4090 generiert:

```
// C4090.c
// compile with: /W1
int *volatile *p;
int *const *q;
int **r;

int main() {
   p = q;   // C4090
   p = r;
   q = p;   // C4090
   q = r;
   r = p;   // C4090
   r = q;   // C4090
}
```