---
title: Compilerfehler C2142
ms.date: 11/04/2016
f1_keywords:
- C2142
helpviewer_keywords:
- C2142
ms.assetid: d0dbe10e-0952-49a4-8b33-e82fb7558b19
ms.openlocfilehash: eda60204e07fd025a8c62b19de70e8204f9f80f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353585"
---
# <a name="compiler-error-c2142"></a>Compilerfehler C2142

unterschiedliche Funktionsdeklarationen, die Variable nur in einer von ihnen angegebene Parameter

Eine Deklaration der Funktion enthält eine Liste der Variable-Parameter. Eine andere Deklaration nicht. ANSI C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) nur.

Im folgende Beispiel wird die C2142 generiert:

```
// C2142.c
// compile with: /Za /c
void func();
void func( int, ... );   // C2142
void func2( int, ... );   // OK
```