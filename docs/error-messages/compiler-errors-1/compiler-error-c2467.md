---
title: Compilerfehler C2467
ms.date: 11/04/2016
f1_keywords:
- C2467
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
ms.openlocfilehash: aa45cbb19519dea7bd5c8fb96abd2c76ea30a786
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302084"
---
# <a name="compiler-error-c2467"></a>Compilerfehler C2467

Ungültige Deklaration des anonymen '– benutzerdefinierte-Typ'

Ein geschachtelter Typ mit den benutzerdefinierten deklariert wurde. Dies ist ein Fehler beim Kompilieren von C-Quellcode mit ANSI-Kompatibilitätsoption ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) aktiviert.

Im folgende Beispiel wird die C2467 generiert:

```
//C2467.c
// compile with: /Za
int main() {
   struct X {
      union { int i; };   // C2467, nested declaration
   };
}
```