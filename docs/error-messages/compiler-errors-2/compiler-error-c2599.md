---
title: Compilerfehler C2599
ms.date: 11/04/2016
f1_keywords:
- C2599
helpviewer_keywords:
- C2599
ms.assetid: 88515f36-7589-47e2-862e-0de8b18d6668
ms.openlocfilehash: 872c3a66d4738c1a69990dffdbbc59cee9e90002
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395468"
---
# <a name="compiler-error-c2599"></a>Compilerfehler C2599

"Enum": Die Vorwärtsdeklaration Enum-Typs ist nicht zulässig.

Der Compiler unterstützt nicht mehr die Vorwärtsdeklaration einer verwalteten Enumeration.

Vorwärtsdeklaration einer Enum-Typs ist nicht zulässig, unter [/Za](../../build/reference/za-ze-disable-language-extensions.md).

Im folgende Beispiel wird der Fehler C2599 generiert:

```
// C2599.cpp
// compile with: /clr /c
enum class Status;   // C2599

enum class Status2 { stop2, hold2, go2};

ref struct MyStruct {
   // Delete the following line to resolve.
   Status m_status;

   Status2 m_status2;   // OK
};

enum class Status { stop, hold, go };
```