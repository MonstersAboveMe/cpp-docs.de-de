---
title: Compilerwarnung (Stufe 1) C4077
ms.date: 11/04/2016
f1_keywords:
- C4077
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
ms.openlocfilehash: 5171ee79c3afd32e847483568fbbf90222747509
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208349"
---
# <a name="compiler-warning-level-1-c4077"></a>Compilerwarnung (Stufe 1) C4077

Unbekannte check_stack-Option

Die alte Form des **check_stack** -Pragmas wird mit einem unbekannten Argument verwendet. Das Argument muss `+`, `-`, `(on)`, `(off)`oder leer sein.

Der Compiler ignoriert das Pragma und die Stapelüberprüfung bleibt unverändert.

## <a name="example"></a>Beispiel

```
// C4077.cpp
// compile with: /W1 /LD
#pragma check_stack yes // C4077
#pragma check_stack +    // Correct old form
#pragma check_stack (on) // Correct new form
```