---
title: Compilerwarnung (Stufe 1) C4812
ms.date: 11/04/2016
f1_keywords:
- C4812
helpviewer_keywords:
- C4812
ms.assetid: a7f5721f-2019-44de-ad62-ed30bac8b1f3
ms.openlocfilehash: 6ba32bf3cad905d686eae78fbfbc198e911e91c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406261"
---
# <a name="compiler-warning-level-1-c4812"></a>Compilerwarnung (Stufe 1) C4812

Veralteter Deklarationsstil: Verwenden Sie stattdessen „new_syntax“.

In der aktuellen Version von Visual C++ wird die explizite Konstruktorspezialisierung noch unterstützt, in einer zukünftigen Version aber möglicherweise nicht mehr.

Im folgenden Beispiel wird C4812 generiert.

```
// C4812.cpp
// compile with: /W1 /c
template <class T>
class MyClass;

template<class T>
class MyClass<T*> {
   MyClass();
};

template<class T>
MyClass<T*>::MyClass<T*>() {}   // C4812
// try the following line instead
// MyClass<T*>::MyClass() {}
```