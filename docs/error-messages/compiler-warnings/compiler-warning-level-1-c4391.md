---
title: Compilerwarnung (Stufe 1) C4391
ms.date: 11/04/2016
f1_keywords:
- C4391
helpviewer_keywords:
- C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
ms.openlocfilehash: d9d1cebe08a6a163d76271ab001ec91b7cee82a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386459"
---
# <a name="compiler-warning-level-1-c4391"></a>Compilerwarnung (Stufe 1) C4391

"Signature": Falscher Rückgabetyp für systeminterne Funktion, erwartet 'type'

Die Deklaration einer Funktion für eine systeminterne Compilerfunktion hatte den falschen Rückgabetyp. Das resultierende Image möglicherweise nicht ordnungsgemäß ausgeführt.

Um diese Warnung zu beheben, korrigieren Sie die Deklaration oder löschen Sie die Deklaration und einfach #include die entsprechende Headerdatei.

Im folgende Beispiel wird die C4391 generiert:

```
// C4391.cpp
// compile with: /W1
// processor: x86
// uncomment the following line and delete the line that
// generated the warning to resolve
// #include "xmmintrin.h"

#ifdef  __cplusplus
extern "C" {
#endif

extern void _mm_load_ss(float *p);   // C4391

#ifdef  __cplusplus
}
#endif

int main()
{
}
```