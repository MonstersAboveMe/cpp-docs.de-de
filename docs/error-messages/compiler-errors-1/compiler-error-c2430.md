---
title: Compilerfehler C2430
ms.date: 11/04/2016
f1_keywords:
- C2430
helpviewer_keywords:
- C2430
ms.assetid: 07c20f76-63e1-4d22-b2a9-98b0d45c5cac
ms.openlocfilehash: 754758e652539e4f2d9b12e568b8ef5ccf41d8db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165696"
---
# <a name="compiler-error-c2430"></a>Compilerfehler C2430

Mehrere Indexregister in "Bezeichner"

Registrieren Sie sich mehr als eine skaliert wird. Der Compiler unterstützt die skalierte Indizierung, aber nur ein Register können zentral hochskalieren.

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C2430 generiert.

```
// C2430.cpp
// processor: x86
int main() {
   _asm mov eax, [ebx*2+ecx*4] // C2430
}
```