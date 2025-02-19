---
title: add_rvalue_reference-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_rvalue_reference
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
ms.openlocfilehash: e5e658f16657c0021b78175e87d122a3accd11eb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411165"
---
# <a name="addrvaluereference-class"></a>add_rvalue_reference-Klasse

Erstellt einen rvalue-Verweistyp des Vorlagenparameters, wenn es sich dabei um einen Objekt- oder Funktionstyp handelt. Ansonsten ist der Typ aufgrund der Semantik der Verweisreduzierung der Gleiche wie der Vorlagenparameter.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der zu ändernde Typ.

## <a name="remarks"></a>Hinweise

Die `add_rvalue_reference` -Klasse verfügt über ein Element mit dem Namen `type`, d.h. ein Alias für den Typ des Rvalue-Verweis auf die Template-Parameter *T*. Die Semantik der verweisreduzierung impliziert, dass für nicht-Objekt und nicht-Funktion *T*, `T&&` ist eine *T*. Zum Beispiel wenn *T* ist ein Lvalue-Verweistyp, `add_rvalue_reference<T>::type` Lvalue-Verweistyp nicht in einen Rvalue-Verweis ist.

Der Einfachheit halber \<Type_traits > eine hilfsprogrammvorlage definiert `add_rvalue_reference_t`, die Aliase der `type` Mitglied `add_rvalue_reference`.

## <a name="example"></a>Beispiel

Dieses Codebeispiel verwendet static_assert, um anzuzeigen, wie rvalue-Verweistypen mithilfe von `add_rvalue_reference` und `add_rvalue_reference_t` erstellt werden, und wie das Ergebnis von `add_rvalue_reference` eines rvalue-Verweistyps kein rvalue-Verweis ist, sondern auf einen lvalue-Typ reduziert wird.

```cpp
// ex_add_rvalue_reference.cpp
// Build by using: cl /EHsc /W4 ex_add_rvalue_reference.cpp
#include <type_traits>
#include <iostream>
#include <string>

using namespace std;
int main()
{
    static_assert(is_same<add_rvalue_reference<string>::type, string&&>::value,
        "Expected add_rvalue_reference_t<string> to be string&&");
    static_assert(is_same<add_rvalue_reference_t<string*>, string*&&>::value,
        "Expected add_rvalue_reference_t<string*> to be string*&&");
    static_assert(is_same<add_rvalue_reference<string&>::type, string&>::value,
        "Expected add_rvalue_reference_t<string&> to be string&");
    static_assert(is_same<add_rvalue_reference_t<string&&>, string&&>::value,
        "Expected add_rvalue_reference_t<string&&> to be string&&");
    cout << "All static_assert tests of add_rvalue_reference passed." << endl;
    return 0;
}

/*Output:
All static_assert tests of add_rvalue_reference passed.
*/
```

## <a name="requirements"></a>Anforderungen

Header: \<type_traits>

Namespace: std

## <a name="see-also"></a>Siehe auch

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_lvalue_reference-Klasse](../standard-library/add-lvalue-reference-class.md)<br/>
[is_rvalue_reference-Klasse](../standard-library/is-rvalue-reference-class.md)<br/>
