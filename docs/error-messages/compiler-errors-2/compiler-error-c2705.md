---
title: Compilerfehler C2705
ms.date: 11/04/2016
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 872471158d3f8c301a271dd68b2ef36839e2b9c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161163"
---
# <a name="compiler-error-c2705"></a>Compilerfehler C2705

'Bezeichnung': Unzulässiger Sprung in den Bereich für "Ausnahmehandlerblock"

Springt zu einer Bezeichnung in einem `try` / `catch`, `__try` / `__except`, `__try` / `__finally` Block. Weitere Informationen finden Sie unter [Ausnahmebehandlung (Task Parallel Library)](../../cpp/exception-handling-in-visual-cpp.md).

Im folgende Beispiel wird die C2705 generiert:

```
// C2705.cpp
int main() {
goto trouble;
   __try {
      trouble: ;   // C2705
   }
   __finally {}

   // try the following line instead
   // trouble: ;
}
```