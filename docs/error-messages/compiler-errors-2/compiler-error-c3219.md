---
title: Compilerfehler C3219
ms.date: 11/04/2016
f1_keywords:
- C3219
helpviewer_keywords:
- C3219
ms.assetid: 9c9757b0-1256-4cdf-9d8c-a3a72f300ce5
ms.openlocfilehash: a93e9ed1a8e00eaecc664bda02a70c81b6c81ded
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243036"
---
# <a name="compiler-error-c3219"></a>Compilerfehler C3219

"param": Der generische Parameter kann nicht von mehreren Nichtschnittstellen eingeschränkt werden: "Klasse".

Es ist nicht zulässig, einen generischen Parameter durch zwei oder mehr verwaltete Klassen einzuschränken.

Im folgenden Beispiel wird C3219 generiert:

```
// C3219.cpp
// compile with: /clr
ref class A {};
ref class B {};

generic <class T>
where T : A, B
ref class E {};   // C3219
```

Das folgende Beispiel zeigt eine mögliche Lösung:

```
// C3219b.cpp
// compile with: /clr /c
ref class A {};

interface struct C {};

generic <class T>
where T : A
ref class E {};
```