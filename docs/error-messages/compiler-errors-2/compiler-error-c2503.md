---
title: Compilerfehler C2503
ms.date: 11/04/2016
f1_keywords:
- C2503
helpviewer_keywords:
- C2503
ms.assetid: da86cc89-fd04-400b-aa8d-a5ffaf7e3918
ms.openlocfilehash: c481a27f19a92f47a19f0cfaa7b59cd509bb3c15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164941"
---
# <a name="compiler-error-c2503"></a>Compilerfehler C2503

'Klasse': Basisklasse kann keine Arrays der Größe Null enthalten

Eine Klasse oder Struktur enthält ein Array der Größe 0 (null). Ein Array in einer Klasse muss über mindestens ein Element verfügen.

Im folgende Beispiel wird die C2503 generiert:

```
// C2503.cpp
// compile with: /c
class A {
   public:
   int array [];
};

class B : A {};    // C2503

class C {
public:
   int array [10];
};

class D : C {};
```