---
title: greater-Struktur
ms.date: 11/04/2016
f1_keywords:
- functional/std::greater
helpviewer_keywords:
- greater struct
- greater function
ms.assetid: ebc348e1-edcd-466b-b21a-db95bd8f9079
ms.openlocfilehash: 7867de3a56893499f8d705e81ac3b34fabcf188c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159482"
---
# <a name="greater-struct"></a>greater-Struktur

Ein binäres Prädikat, mit dem der größer-als-Vorgang (`operator>`) auf den Argumenten ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
template <class Type = void>
struct greater : public binary_function <Type, Type, bool>
{
    bool operator()(
    const Type& Left,
    const Type& Right) const;

};

// specialized transparent functor for operator>
template <>
struct greater<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const
    ->  decltype(std::forward<T>(Left)> std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parameter

*Typ*, *T*, *U* jeder Typ, unterstützt eine `operator>` , das Operanden angegebener oder abgeleiteter Typen akzeptiert.

*Links*<br/>
Der linke Operand des größer-als-Vorgangs. Die nicht spezialisierte Vorlage besitzt ein Lvalue-Verweisargument vom Typ *Typ*. Die spezialisierte Vorlage vervollkommnet die Weiterleitung von Lvalue und Rvalue-verweisargumenten des abgeleiteten Typs *T*.

*Rechts*<br/>
Der rechte Operand des größer-als-Vorgangs. Die nicht spezialisierte Vorlage besitzt ein Lvalue-Verweisargument vom Typ *Typ*. Die spezialisierte Vorlage vervollkommnet die Weiterleitung von Lvalue und Rvalue-verweisargumenten des abgeleiteten Typs *U*.

## <a name="return-value"></a>Rückgabewert

Das Ergebnis von `Left > Right`. Die spezialisierte Vorlage vervollkommnet die Weiterleitung des Ergebnisses mit dem von `operator>` zurückgegebenen Typs.

## <a name="remarks"></a>Hinweise

Das binäre Prädikat `greater` <  `Type`> stellt eine strenge schwache Sortierung eines Satzes von Elementwerten vom Typ *Typ* in Äquivalenzklassen, wenn dieser Typ den mathematischen Standard erfüllt Anforderungen für so sortiert wird. Die Spezialisierungen für einen Zeigertyp ergeben eine gesamte Sortierung von Elementen, insofern, dass alle Elemente unterschiedlicher Werte zueinander in Beziehung stehend sortiert werden.

## <a name="example"></a>Beispiel

```cpp
// functional_greater.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <cstdlib>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i < 8 ; i++ )
   {
      v1.push_back( rand( ) );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // specify binary predicate greater<int>( )
   sort( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (41 18467 6334 26500 19169 15724 11478 29358)
Sorted vector v1 = (41 6334 11478 15724 18467 19169 26500 29358)
Resorted vector v1 = (29358 26500 19169 18467 15724 11478 6334 41)
```

## <a name="requirements"></a>Anforderungen

**Header:** \<functional>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[C++-Standardbibliotheksreferenz](../standard-library/cpp-standard-library-reference.md)<br/>
