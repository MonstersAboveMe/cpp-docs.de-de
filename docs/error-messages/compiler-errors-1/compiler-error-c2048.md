---
title: Compilerfehler C2048
ms.date: 11/04/2016
f1_keywords:
- C2048
helpviewer_keywords:
- C2048
ms.assetid: 44704726-85fc-42f0-afb9-194df8c4ca7c
ms.openlocfilehash: 2cdb151d882d7b494e8d32494b0b3c8c62e01b3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408861"
---
# <a name="compiler-error-c2048"></a>Compilerfehler C2048

Mehrere Vorkommen von default

Eine `switch` -Anweisung enthält mehrere `default` -Bezeichnungen. Löschen Sie eine der `default` Bezeichnungen, um den Fehler zu beheben.

Im folgenden Beispiel wird C2048 generiert:

```
// C2048.cpp
int main() {
   int a = 1;
   switch (a) {
      case 1:
         a = 0;
      default:
         a = 2;
      default:   // C2048
         a = 3;
   }
}
```

Mögliche Lösung:

```
// C2048b.cpp
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