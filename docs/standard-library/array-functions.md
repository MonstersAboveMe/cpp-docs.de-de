---
title: '&lt;array&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- array/std::array::get
- array/std::get
- array/std::swap
ms.assetid: e0700a33-a833-4655-8735-16e71175efc8
helpviewer_keywords:
- std::array [C++], get
- std::get [C++]
- std::swap [C++]
ms.openlocfilehash: 719377be2ac130100e3f9e9ea608c5c27be3101f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377269"
---
# <a name="ltarraygt-functions"></a>&lt;array&gt;-Funktionen

Die \<Array >-Header enthält zwei nicht-Memberfunktionen, `get` und `swap`, arbeiten auf **Array** Objekte.

|||
|-|-|
|[get](#get)|[swap](#swap)|

## <a name="get"></a> get

Gibt einen Verweis auf das angegebene Element des Arrays zurück.

```cpp
template <int Index, class T, size_t N>
constexpr T& get(array<T, N>& arr) noexcept;

template <int Index, class T, size_t N>
constexpr const T& get(const array<T, N>& arr) noexcept;

template <int Index, class T, size_t N>
constexpr T&& get(array<T, N>&& arr) noexcept;
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Der Offset des Elements.

*T*<br/>
Der Typ eines Elements.

*N*<br/>
Die Anzahl der Elemente im Array.

*arr*<br/>
Das Array, aus dem die Auswahl erfolgt.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

using namespace std;

typedef array<int, 4> MyArray;

int main()
{
    MyArray c0 { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& e : c0)
    {
        cout << " " << e;
    }
    cout << endl;

    // display odd elements " 1 3"
    cout << " " << get<1>(c0);
    cout << " " << get<3>(c0) << endl;
}
```

```Output
0 1 2 3
1 3
```

## <a name="swap"></a>  swap

Eine nicht-Member-vorlagenspezialisierung von `std::swap` , die tauscht zwei **Array** Objekte.

```cpp
template <class Ty, std::size_t N>
void swap(array<Ty, N>& left, array<Ty, N>& right);
```

### <a name="parameters"></a>Parameter

*Ty*<br/>
Der Typ eines Elements.

*N*<br/>
Die Größe des Arrays.

*left*<br/>
Das erste auszutauschende Array.

*right*<br/>
Das zweite auszutauschende Array.

### <a name="remarks"></a>Hinweise

Die Vorlagenfunktion führt `left.swap(right)` aus.

### <a name="example"></a>Beispiel

```cpp
// std__array__swap.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = { 4, 5, 6, 7 };
    c0.swap(c1);

    // display swapped contents " 4 5 6 7"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    swap(c0, c1);

    // display swapped contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="see-also"></a>Siehe auch

[\<array>](../standard-library/array.md)<br/>
