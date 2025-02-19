---
title: Compilerfehler C3767
ms.date: 11/04/2016
f1_keywords:
- C3767
helpviewer_keywords:
- C3767
ms.assetid: 5247cdcd-639c-4527-bd37-37e74c4e8fab
ms.openlocfilehash: 61f7479986cccfa3851d85bf8e7bc0e9da3d1cea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400200"
---
# <a name="compiler-error-c3767"></a>Compilerfehler C3767

'Funktion': Auf mögliche Funktion(en) kann nicht zugegriffen werden

Bei einer in einer Klasse definierten Friend-Funktion wird nicht davon ausgegangen, dass sie so behandelt wird, als wäre sie im globalen Gültigkeitsbereich des Namespaces definiert und deklariert worden. Sie kann jedoch mittels einer argumentbezogenen Suche gefunden werden.

C3767 kann auch von einer wichtigen Änderung verursacht werden: systemeigene Typen sind nun standardmäßig im privaten eine **"/ CLR"** Kompilierung; Siehe [Geben Sie die Sichtbarkeit](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) für Weitere Informationen.

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C3767 generiert:

```
// C3767a.cpp
// compile with: /clr
using namespace System;
public delegate void TestDel();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;
};

public ref class MyClass2 : public MyClass {
public:
   void Test() {
      MyClass^ patient = gcnew MyClass;
      patient->MyClass_Event();
    }
};

int main() {
   MyClass^ x = gcnew MyClass;
   x->MyClass_Event();   // C3767

   // OK
   MyClass2^ y = gcnew MyClass2();
   y->Test();
};
```

Im folgende Beispiel wird die C3767 generiert:

```
// C3767c.cpp
// compile with: /clr /c

ref class Base  {
protected:
   void Method() {
      System::Console::WriteLine("protected");
   }
};

ref class Der : public Base {
   void Method() {
      ((Base^)this)->Method();   // C3767
      // try the following line instead
      // Base::Method();
   }
};
```

