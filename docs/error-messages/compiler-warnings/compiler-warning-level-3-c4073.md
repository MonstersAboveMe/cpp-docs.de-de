---
title: Compilerwarnung (Stufe 3) C4073
ms.date: 11/04/2016
f1_keywords:
- C4073
helpviewer_keywords:
- C4073
ms.assetid: 50081a6e-6acd-45ff-8484-9b1ea926cc5c
ms.openlocfilehash: db39f76f9bfdd46c300ea6e3738a63b636fe0a03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402332"
---
# <a name="compiler-warning-level-3-c4073"></a>Compilerwarnung (Stufe 3) C4073

Fügen Sie Initialisierungen in Initialisierungsbereich einer Bibliothek

Nur die Bibliotheken von Drittanbietern-Entwickler sollten die Initialisierungsbereich einer Bibliothek, verwenden, die angegebenen [#pragma Init_seg](../../preprocessor/init-seg.md). Im folgende Beispiel wird die C4073 generiert:

```
// C4073.cpp
// compile with: /W3
#pragma init_seg(lib)   // C4073

// try this line to resolve the warning
// #pragma init_seg(user)

int main() {
}
```