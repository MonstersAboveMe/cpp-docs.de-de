---
title: Compilerfehler C2039
ms.date: 11/04/2016
f1_keywords:
- C2039
helpviewer_keywords:
- C2039
ms.assetid: f9dfd521-9b36-4454-a69c-d63f45b606bb
ms.openlocfilehash: ff795a551c091deb73c5fae1e3b67a61d9966ff0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266854"
---
# <a name="compiler-error-c2039"></a>Compilerfehler C2039

'Bezeichner1': ist kein Member von 'Bezeichner2'

Ein Member einer Struktur, Klasse oder Union wird vom Code nicht korrekt aufgerufen, oder es wird nicht ordnungsgemäß auf diesen Member verwiesen.

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C2039 generiert.

```
// C2039.cpp
struct S {
   int mem0;
} s, *pS = &s;

int main() {
   pS->mem1 = 0;   // C2039 mem1 is not a member
   pS->mem0 = 0;   // OK
}
```

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C2039 generiert.

```
// C2039_b.cpp
// compile with: /clr
using namespace System;
int main() {
   Console::WriteLine( "{0}", DateTime::get_Now());   // C2039
   Console::WriteLine( "{0}", DateTime::Now);   // OK
   Console::WriteLine( "{0}", DateTime::Now::get());   // OK
}
```

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C2039 generiert.

```
// C2039_c.cpp
// compile with: /clr /c
ref struct S {
   property int Count {
     int get();
     void set(int i){}
   };
};

int S::get_Count() { return 0; }   // C2039
int S::Count::get() { return 0; }   // OK
```

## <a name="example"></a>Beispiel

C2039 kann auch auftreten, wenn Sie auf einen Standardindexer falsch zuzugreifen. Im folgenden Beispiel wird eine in C# erstellte Komponente definiert.

```
// C2039_d.cs
// compile with: /target:library
// a C# program
[System.Reflection.DefaultMember("Item")]
public class B {
   public int Item {
      get { return 13; }
      set {}
   }
};
```

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C2039 generiert.

```
// C2039_e.cpp
// compile with: /clr
using namespace System;
#using "c2039_d.dll"

int main() {
   B ^ b = gcnew B;
   int n = b->default;   // C2039
   // try the following line instead
   // int n = b->Item;
   Console::WriteLine(n);
}
```

## <a name="example"></a>Beispiel

C2039 kann auch auftreten, wenn Sie Generics verwenden. Im folgende Beispiel wird die C2039 generiert.

```
// C2039_f.cpp
// compile with: /clr
interface class I {};

ref struct R : public I {
   virtual void f3() {}
};

generic <typename T>
where T : I
void f(T t) {
   t->f3();   // C2039
   safe_cast<R^>(t)->f3();   // OK
}

int main() {
   f(gcnew R());
}
```

## <a name="example"></a>Beispiel

C2039 kann auftreten, wenn Sie versuchen, verwaltete oder nicht verwaltete Ressourcen freizugeben. Weitere Informationen finden Sie unter [Destruktoren und Finalizer](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Im folgende Beispiel wird die C2039 generiert.

```
// C2039_g.cpp
// compile with: /clr
using namespace System;
using namespace System::Threading;

void CheckStatus( Object^ stateInfo ) {}

int main() {
   ManualResetEvent^ event = gcnew ManualResetEvent( false );
   TimerCallback^ timerDelegate = gcnew TimerCallback( &CheckStatus );
   Timer^ stateTimer = gcnew Timer( timerDelegate, event, 1000, 250 );

   ((IDisposable ^)stateTimer)->Dispose();   // C2039

   stateTimer->~Timer();   // OK
}
```