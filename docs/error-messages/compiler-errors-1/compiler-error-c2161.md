---
title: Compilerfehler C2161
ms.date: 11/04/2016
f1_keywords:
- C2161
helpviewer_keywords:
- C2161
ms.assetid: d6798821-13bb-4e60-924f-85f7bf955387
ms.openlocfilehash: 366e848d566dbcbf9414565de604aa722f758456
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174804"
---
# <a name="compiler-error-c2161"></a>Compilerfehler C2161

"##" kann nicht am Ende einer Makrodefinition stehen

Eine Makrodefinition endete mit einem tokeneinfügenden Operator (##).

Im folgenden Beispiel wird C2161 generiert:

```
// C2161.cpp
// compile with: /c
#define mac(a,b) a   // OK
#define mac(a,b) a##   // C2161
```