---
title: Is_invocable, Is_invocable_r, Is_nothrow_invocable, Is_nothrow_invocable_r-Klassen
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::is_invocable
- type_traits/std::is_invocable_r
- type_traits/std::is_nothrow_invocable
- type_traits/std::is_nothrow_invocable_r
helpviewer_keywords:
- is_invocable class
- is_invocable
- is_invocable_r class
- is_invocable_r
- is_nothrow_invocable class
- is_nothrow_invocable
- is_nothrow_invocable_r class
- is_nothrow_invocable_r
ms.openlocfilehash: bb5e75a897029ded2e00e491d93d2df41a3e115b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336230"
---
# <a name="isinvocable-isinvocabler-isnothrowinvocable-isnothrowinvocabler-classes"></a>Is_invocable, Is_invocable_r, Is_nothrow_invocable, Is_nothrow_invocable_r-Klassen

Diese Vorlagen bestimmen, ob ein Typ mit den angegebenen Argumenttypen aufgerufen werden kann. `is_invocable_r` und `is_nothrow_invocable_r` außerdem ermitteln, ob das Ergebnis des Aufrufs für einen bestimmten Typ konvertiert werden. `is_nothrow_invocable` und `is_nothrow_invocable_r` außerdem ermitteln, ob der Aufruf bekannt ist, nicht, dass Ausnahmen auslösen. In C ++ 17-hinzugefügt.

## <a name="syntax"></a>Syntax

```cpp
template <class Callable, class... Args>
struct is_invocable;

template <class Convertible, class Callable, class... Args>
struct is_invocable_r;

template <class Callable, class... Args>
struct is_nothrow_invocable;

template <class Convertible, class Callable, class... Args>
struct is_nothrow_invocable_r;

// Helper templates
template <class Callable, class... Args>
inline constexpr bool is_invocable_v =
    std::is_invocable<Callable, Args...>::value;

template <class Convertible, class Callable, class... Args>
inline constexpr bool is_invocable_r_v =
    std::is_invocable_r<Convertible, Callable, Args...>::value;

template <class Callable, class... Args>
inline constexpr bool is_nothrow_invocable_v =
    std::is_nothrow_invocable<Callable, Args...>::value;

template <class Convertible, class Callable, class... Args>
inline constexpr bool is_nothrow_invocable_r_v =
    std::is_nothrow_invocable_r<Convertible, Callable, Args...>::value;
```

### <a name="parameters"></a>Parameter

*aufrufbare*<br/>
Der abzufragende, aufgerufene Typ.

*Args*<br/>
Die Argumenttypen abgefragt werden soll.

*Konvertiert werden kann.*<br/>
Der Typ das Ergebnis der *Callable* konvertierbar sein muss.

## <a name="remarks"></a>Hinweise

Die `is_invocable` typprädikats ist true, wenn die aufrufbarer Typ *Callable* kann mit den Argumenten aufgerufen werden *Args* in einem nicht ausgewerteten Kontext.

Die `is_invocable_r` typprädikats ist true, wenn die aufrufbarer Typ *Callable* kann mit den Argumenten aufgerufen werden *Args* in einem nicht ausgewerteten Kontext erzeugt ein Ergebnis Typ konvertiert werden kann,  *Konvertiert werden kann*.

Die `is_nothrow_invocable` typprädikats ist true, wenn die aufrufbarer Typ *Callable* kann mit den Argumenten aufgerufen werden *Args* solch ein Aufruf wird in einem nicht ausgewerteten Kontext und die nicht zum Auslösen einer Ausnahme bezeichnet.

Die `is_nothrow_invocable_r` typprädikats ist true, wenn die aufrufbarer Typ *Callable* kann mit den Argumenten aufgerufen werden *Args* in einem nicht ausgewerteten Kontext erzeugt ein Ergebnis Typ konvertiert werden kann,  *Konvertiert werden kann.*, und dass es sich bei solch ein Aufruf bekannt ist, nicht um eine Ausnahme auszulösen.

Alle Typen *konvertiert werden kann.*, *Callable*, und die Typen im parameterpaket *Args* muss ein vollständiger Typ, ein Array mit Unbekannter Grenze oder eine möglicherweise cv-qualifizierte **"void"**. Das Verhalten des Prädikats ist, andernfalls nicht definiert.

## <a name="example"></a>Beispiel

```cpp
// std__type_traits__is_invocable.cpp
// compile using: cl /EHsc /std:c++17 std__type_traits__is_invocable.cpp
#include <type_traits>

auto test1(int) noexcept -> int (*)()
{
    return nullptr;
}

auto test2(int) -> int (*)()
{
    return nullptr;
}

int main()
{
    static_assert( std::is_invocable<decltype(test1), short>::value );

    static_assert( std::is_invocable_r<int(*)(), decltype(test1), int>::value ); 
    static_assert( std::is_invocable_r<long(*)(), decltype(test1), int>::value ); // fails

    static_assert( std::is_nothrow_invocable<decltype(test1), int>::value );
    static_assert( std::is_nothrow_invocable<decltype(test2), int>::value ); // fails

    static_assert( std::is_nothrow_invocable_r<int(*)(), decltype(test1), int>::value );
    static_assert( std::is_nothrow_invocable_r<int(*)(), decltype(test2), int>::value ); // fails
}
```

## <a name="requirements"></a>Anforderungen

**Header:** \<type_traits>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[<type_traits>](../standard-library/type-traits.md)<br/>
[invoke](functional-functions.md#invoke)<br/>
