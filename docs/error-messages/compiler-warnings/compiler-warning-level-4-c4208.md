---
title: Compilerwarnung (Stufe 4) C4208
ms.date: 11/04/2016
f1_keywords:
- C4208
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
ms.openlocfilehash: 11c6b1ad50c44ac4ad2a9d014e57efef097d9d8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401175"
---
# <a name="compiler-warning-level-4-c4208"></a>Compilerwarnung (Stufe 4) C4208

nicht dem Standard entsprechende Erweiterung: Delete [Ausdruck] - Ausdruck ausgewertet, aber ignoriert

Mit Microsoft-Erweiterungen (/ Ze), können Sie ein Array mit einem Wert in Klammern mit Löschen der [delete-Operator](../../cpp/delete-operator-cpp.md). Der Wert wird ignoriert.

```
// C4208.cpp
// compile with: /W4
int main()
{
   int * MyArray = new int[18];
   delete [18] MyArray;      // C4208
   MyArray = new int[18];
   delete [] MyArray;        // ok
}
```

Diese Werte sind ungültig, ANSI-Kompatibilität ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).