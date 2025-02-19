---
title: make_public
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
ms.openlocfilehash: d569758f90b9e55f65ad13517f86dea41d151ca8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371762"
---
# <a name="makepublic"></a>make_public
Gibt an, dass für einen systemeigenen Typ der öffentliche Assemblyzugriff gewährt wird.

## <a name="syntax"></a>Syntax

```
#pragma make_public(type)
```

### <a name="parameters"></a>Parameter

*Typ* ist der Name des Typs öffentliche Assemblyzugriff gewährt werden soll.

## <a name="remarks"></a>Hinweise

**Make_public** ist nützlich, wenn der systemeigene Typ, die Sie verweisen möchten aus einer h-Datei ist, die Sie nicht ändern können. Soll der systemeigene Typ in der Signatur einer öffentlichen Funktion in einem Typ mit öffentlicher Assemblysichtbarkeit verwendet werden, muss der systemeigene Typ auch über den öffentlichen Assemblyzugriff verfügen, sonst gibt der Compiler eine Warnung aus.

**Make_public** muss im globalen Gültigkeitsbereich angegeben werden, und ist nur an dem Punkt am Ende der Quellcodedatei an die It über deklariert ist.

Der systemeigene Typ kann implizit oder explizit privat sein; finden Sie unter [Typsichtbarkeit](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) für Weitere Informationen.

## <a name="examples"></a>Beispiele

Beim folgenden Beispiel handelt es sich um die Inhalte einer H-Datei, welche die Definitionen für zwei systemeigene Strukturen enthält.

```cpp
// make_public_pragma.h
struct Native_Struct_1 { int i; };
struct Native_Struct_2 { int i; };
```

Das folgende Codebeispiel verwendet die Headerdatei und zeigt, es sei denn, Sie explizit die systemeigenen Strukturen als öffentlich kennzeichnen mit **Make_public**, generiert der Compiler eine Warnung, wenn Sie versuchen, verwenden die systemeigenen Strukturen in der die Signatur einer öffentlicher Funktion in einem öffentlich verwalteten Typ.

```cpp
// make_public_pragma.cpp
// compile with: /c /clr /W1
#pragma warning (default : 4692)
#include "make_public_pragma.h"
#pragma make_public(Native_Struct_1)

public ref struct A {
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692
};
```

## <a name="see-also"></a>Siehe auch

[Pragma-Direktiven und das __Pragma-Schlüsselwort](../preprocessor/pragma-directives-and-the-pragma-keyword.md)