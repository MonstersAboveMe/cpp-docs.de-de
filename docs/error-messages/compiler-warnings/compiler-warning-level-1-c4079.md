---
title: Compilerwarnung (Stufe 1) C4079
ms.date: 11/04/2016
f1_keywords:
- C4079
helpviewer_keywords:
- C4079
ms.assetid: 549759f0-e168-47e9-8c9a-de93ac843689
ms.openlocfilehash: 8f9a9e05ab2a65ad954f9928f7b9fab0e7fee9cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207524"
---
# <a name="compiler-warning-level-1-c4079"></a>Compilerwarnung (Stufe 1) C4079

Unerwartetes Token "Token"

Ein Token unerwartete Trennzeichen tritt auf, in einer Argumentliste des Pragmas. Der Rest des Pragmas wurde ignoriert.

Im folgende Beispiel wird die C4079 generiert:

```
// C4079.cpp
// compile with: /W1
#pragma warning(disable : 4081)
#pragma pack(c,16)   // C4079

int main() {
}
```