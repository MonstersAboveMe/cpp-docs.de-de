---
title: Compilerfehler C3408
ms.date: 11/04/2016
f1_keywords:
- C3408
helpviewer_keywords:
- C3408
ms.assetid: 1f5ea979-fb1e-4214-b310-6fd6ca8249b1
ms.openlocfilehash: c374ea60129b315caf4b72dbf2917a9f4c4ba2ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353003"
---
# <a name="compiler-error-c3408"></a>Compilerfehler C3408

'attribut': Das Attribut ist für Vorlagendefinitionen nicht zulässig.

Attribute können nicht auf Vorlagendefinitionen angewendet werden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3408 generiert:

```
// C3408.cpp
// compile with: /c
template <class T> struct PTS {
   enum {
      IsPointer = 0,
      IsPointerToDataMember = 0
   };
};

template <class T>
[coclass]   // C3408
struct PTS<T*> {
   enum {
      IsPointer = 1,
      IsPointerToDataMember = 0
   };
};

template
<class T, class U>
struct PTS<T U::*> {
   enum {
      IsPointer = 1,
      IsPointerToDataMember = 1
   };
};

struct S{};

extern "C" int printf(const char*,...);

int main() {
   S s, *pS;
   int S::*ptm;

   printf("PTS<S>::IsPointer == %d PTS<S>::IsPointerToDataMember == %d\n", PTS<S>::IsPointer, PTS<S>:: IsPointerToDataMember);
   printf("PTS<S*>::IsPointer == %d PTS<S*>::IsPointerToDataMember == %d\n", PTS<S*>::IsPointer, PTS<S*>:: IsPointerToDataMember);
   printf("PTS<int S::*>::IsPointer == %d PTS<int S::*>::IsPointerToDataMember == %d\n", PTS<int S::*>::IsPointer, PTS<int S::*>:: IsPointerToDataMember);
}
```