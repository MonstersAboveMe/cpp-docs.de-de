---
title: Compilerwarnung (Stufe 1) C4215
ms.date: 11/04/2016
f1_keywords:
- C4215
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
ms.openlocfilehash: a45cd6cf86eb8ab1edb33ad5e0df8374972c425e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386485"
---
# <a name="compiler-warning-level-1-c4215"></a>Compilerwarnung (Stufe 1) C4215

nicht dem Standard entsprechende Erweiterung: long float

Die Standard-Microsoft-Erweiterungen (/ Ze) behandeln **long float** als **doppelte**. ANSI-Kompatibilität ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) nicht. Verwendung **doppelte** um die Kompatibilität aufrechtzuerhalten.

Im folgende Beispiel wird die C4215 generiert:

```
// C4215.cpp
// compile with: /W1 /LD
long float a;   // C4215

// use the line below to resolve the warning
// double a;
```