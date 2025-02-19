---
title: '&lt;type_traits&gt;-Typedefs'
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::false_type
- xtr1common/std::false_type
- type_traits/std::true_type
- xtr1common/std::true_type
ms.assetid: 8ac040ca-ed2d-4570-adc9-cb5626530053
ms.openlocfilehash: 579d276b7e9f2a7b44b41681b85fffd318ecddbb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278994"
---
# <a name="lttypetraitsgt-typedefs"></a>&lt;type_traits&gt;-Typedefs

|||
|-|-|
|[false_type](#false_type)|[true_type](#true_type)|

## <a name="false_type"></a> false_type-Typedef

Enthält eine Ganzzahlkonstante mit einem falschen Wert.

```cpp
typedef integral_constant<bool, false> false_type;
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Synonym für eine Spezialisierung der Vorlage `integral_constant`.

### <a name="example"></a>Beispiel

```cpp
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="true_type"></a> true_type-Typedef

Enthält eine Ganzzahlkonstante mit einem wahren Wert.

```cpp
typedef integral_constant<bool, true> true_type;
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Synonym für eine Spezialisierung der Vorlage `integral_constant`.

### <a name="example"></a>Beispiel

```cpp
// std__type_traits__true_type.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="see-also"></a>Siehe auch

[<type_traits>](../standard-library/type-traits.md)<br/>
