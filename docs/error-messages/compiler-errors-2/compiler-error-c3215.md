---
title: Compilerfehler C3215
ms.date: 11/04/2016
f1_keywords:
- C3215
helpviewer_keywords:
- C3215
ms.assetid: d0d16007-8885-42e0-b086-2d3a61f348c5
ms.openlocfilehash: 24f17d2990c9258168a6d37fef101c21f62cb08d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778721"
---
# <a name="compiler-error-c3215"></a>Compilerfehler C3215

"Typ1": Der generische Typparameter wird bereits von "Typ2" eingeschränkt.

Eine Einschränkung wurde mehrmals angegeben.

Weitere Informationen zu Generika finden Sie unter [Generics](../../extensions/generics-cpp-component-extensions.md).

Im folgenden Beispiel wird C3215 generiert:

```
// C3215.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where T : A,A
ref class C {};   // C3215
```

Mögliche Lösung:

```
// C3215b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
where T : A
ref class C {};
```