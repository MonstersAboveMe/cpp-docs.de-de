---
title: Compilerfehler C3235
ms.date: 11/04/2016
f1_keywords:
- C3235
helpviewer_keywords:
- C3235
ms.assetid: 0554d6c7-e1dc-4c99-8934-cbcf491c8203
ms.openlocfilehash: 1e74d479e75aee98dada16107b7e33d5cfe0c0cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174145"
---
# <a name="compiler-error-c3235"></a>Compilerfehler C3235

"Spezialisierung": Die explizite oder teilweise Spezialisierung einer generischen Klasse ist nicht zulässig.

Generische Klassen können nicht für explizite oder teilweise Spezialisierungen verwendet werden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3235 generiert.

```
// C3235.cpp
// compile with: /clr
generic<class T>
public ref class C {};

generic<>
public ref class C<int> {};   // C3235 Remove this specialization to resolve this error.
```