---
title: Compilerfehler C2319
ms.date: 11/04/2016
f1_keywords:
- C2319
helpviewer_keywords:
- C2319
ms.assetid: 25263e6e-f5ba-4d2c-8727-8c2d8ca2e5ce
ms.openlocfilehash: f0ec35cfb74fd08180969344180ff42d485d58c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404298"
---
# <a name="compiler-error-c2319"></a>Compilerfehler C2319

Auf 'try/catch' muss eine zusammengesetzte Anweisung folgen. '{' fehlt

Es wurde kein `try` - oder `catch` -Block gefunden, der auf die `try` - oder `catch` -Anweisung folgt. Der Block muss in geschweifte Klammern eingeschlossen werden.

Im folgenden Beispiel wird C2319 generiert:

```
// C2319.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
   try {
      throw "ooops!";
   }
   catch( C ) ;    // C2319
   // try the following line instead
   // catch( C ) {}
}
```