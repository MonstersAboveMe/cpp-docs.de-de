---
title: Compilerfehler C2050
ms.date: 11/04/2016
f1_keywords:
- C2050
helpviewer_keywords:
- C2050
ms.assetid: 66aaed7d-00db-4ce1-a9d6-4447c1cf07ce
ms.openlocfilehash: 99091452c2fc845ba396d7a8b290c2c857146257
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408900"
---
# <a name="compiler-error-c2050"></a>Compilerfehler C2050

Switch-Ausdruck ist keine Ganzzahl

Die `switch` Ausdruck ergibt einen nicht ganzzahligen Wert. Verwenden Sie nur ganzzahlige Werte im Switch-Anweisungen, um den Fehler zu beheben.

Im folgende Beispiel wird die C2050 generiert:

```
// C2050.cpp
int main() {
   int a = 1;
   switch ("a") {   // C2050
      case 1:
         a = 0;
      default:
         a = 2;
   }
}
```

Mögliche Lösung:

```
// C2050b.cpp
int main() {
   int a = 1;
   switch (a) {
      case 1:
         a = 0;
      default:
         a = 2;
   }
}
```