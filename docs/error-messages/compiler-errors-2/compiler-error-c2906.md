---
title: Compilerfehler C2906
ms.date: 11/04/2016
f1_keywords:
- C2906
helpviewer_keywords:
- C2906
ms.assetid: 30f652f1-6af6-4a2f-a69e-a1a4876cc8c6
ms.openlocfilehash: 621b31cf362c1dcc740390cf9e405b7da3f05da8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378517"
---
# <a name="compiler-error-c2906"></a>Compilerfehler C2906

"Spezialisierung": explizite Spezialisierung erfordert "Vorlage <>"

Sie müssen die neue Syntax für die explizite Spezialisierung von Vorlagen verwenden.

Im folgende Beispiel wird die C2906 generiert:

```
// C2906.cpp
// compile with: /c
template<class T> class X{};   // primary template
class X<int> { }   // C2906
template<> class X<int> { };   // new syntax
```