---
title: Compilerwarnung (Stufe 4) C4032
ms.date: 11/04/2016
f1_keywords:
- C4032
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
ms.openlocfilehash: fa1602d63ed9822725fea8e1b842929f221d3926
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401461"
---
# <a name="compiler-warning-level-4-c4032"></a>Compilerwarnung (Stufe 4) C4032

formaler Parameter 'Nummer' hat einen anderen Typ, wenn die höher gestuft

Der Parametertyp ist nicht kompatibel ist, über Standard-Erweiterungen, mit dem Typ in einer früheren Deklaration.

Dies ist ein Fehler in ANSI C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) und eine Warnung der Microsoft-Erweiterungen (/ Ze).

## <a name="example"></a>Beispiel

```
// C4032.c
// compile with: /W4
void func();
void func(char);   // C4032, char promotes to int

int main()
{
}
```