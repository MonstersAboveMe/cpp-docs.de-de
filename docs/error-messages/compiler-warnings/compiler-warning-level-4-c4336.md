---
title: Compilerwarnung (Stufe 4) C4336
ms.date: 11/04/2016
f1_keywords:
- C4336
helpviewer_keywords:
- C4336
ms.assetid: 93f199dd-d6dd-42c0-82d8-c12d101a7235
ms.openlocfilehash: 4946b932fa897dab057e430f16c781e2d06bebd0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400850"
---
# <a name="compiler-warning-level-4-c4336"></a>Compilerwarnung (Stufe 4) C4336

Importieren Sie zuerst die übergreifende Typbibliothek "Typbibliothek1", bevor Sie "Typbibliothek2" Importieren

Eine Typbibliothek mit verwiesen wurde, wird die [#import](../../preprocessor/hash-import-directive-cpp.md) Richtlinie. Die Typbibliothek enthalten einen Verweis auf eine andere Typbibliothek, die nicht in referenziert wurde `#import`. Diese anderen TLB-Datei wurde vom Compiler gefunden.

Zwei Typbibliotheken auf dem Datenträger, die von den folgenden zwei Dateien (kompiliert mit midl.exe) erstellt:

```
// c4336a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library c4336aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C4336
   {
      one, two, three
   };
};
```

Die zweite Typbibliothek:

```
// c4336b.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4336bLib
{
   importlib ("c4336a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4336
   {
      enum E_C4336 e;
   };
};
```

Im folgende Beispiel wird die C4336 generiert:

```
// C4336.cpp
// compile with: /W4 /LD
// #import "C4336a.tlb"
#import "C4336b.tlb"   // C4336, uncomment previous line to resolve
```