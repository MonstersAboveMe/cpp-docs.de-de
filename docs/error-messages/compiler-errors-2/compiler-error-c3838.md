---
title: Compilerfehler C3838
ms.date: 11/04/2016
f1_keywords:
- C3838
helpviewer_keywords:
- C3838
ms.assetid: d6f470c2-131a-4a8c-843a-254acd43da83
ms.openlocfilehash: c8664c9df837d44ab6e356d54ff9e35c3776778a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208082"
---
# <a name="compiler-error-c3838"></a>Compilerfehler C3838

von 'Type' kann nicht explizit geerbt werden.

Das angegebene `type` kann nicht in einer Klasse als Basisklasse dienen.

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C3838 generiert:

```
// C3838a.cpp
// compile with: /clr /c
public ref class B : public System::Enum {};   // C3838
```
