---
title: Compilerfehler C3392
ms.date: 11/04/2016
f1_keywords:
- C3392
helpviewer_keywords:
- C3392
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
ms.openlocfilehash: 72bdef1b3344b3d69ba0d014f92a85e9381de4b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243023"
---
# <a name="compiler-error-c3392"></a>Compilerfehler C3392

'Typargument': Ungültiges Typargument für den generischen 'Param'-Parameter von 'generischer_Typ' (generisch). Muss einen öffentlichen parameterlosen Konstruktor aufweisen.

Ein generischer Typ wurde fehlerhaft instanziiert. Überprüfen Sie die Typdefinition. Weitere Informationen finden Sie unter [Generika](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Beispiel

Im folgende Beispiel wird c# verwendet eine Komponente zu erstellen, die einen generischen Typ mit bestimmten Einschränkungen, die beim Erstellen von generischer Typen in C++ nicht unterstützt werden, enthält c++ / CLI. Weitere Informationen finden Sie unter [Einschränkungen für Typparameter](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```cs
// C3392.cs
// Compile by using: csc /target:library C3392.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Wenn die Komponente C3392.dll verfügbar ist, im folgende Beispiel wird C3392 generiert:

```cpp
// C3392_b.cpp
// Compile by using: cl /clr C3392_b.cpp
#using <C3392.dll>

ref class R { R(int) {} };
ref class N { N() {} };

value class V {};

ref class N2 { public: N2() {} };
ref class R2 { public: R2() {} };

int main () {
   GR<R^, V, N^>^ gr1;   // C3392
   GR<R^, V, N2^>^ gr1a; // OK

   GR<R^, N^, N^>^ gr3;  // C3392
   GR<R^, V, N2^>^ gr3a; // OK

   GR<R^, V, R^>^ gr4;   // C3392
   GR<R^, V, R2^>^ gr4a; // OK
}
```