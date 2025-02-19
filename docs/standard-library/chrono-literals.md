---
title: chrono-Literale
ms.date: 11/04/2016
ms.assetid: 1a9e23b1-256f-4570-8226-5fa7364fb032
ms.openlocfilehash: 838ae99f5a21660968e0215818aa959348f38305
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279137"
---
# <a name="chrono-literals"></a>chrono-Literale

(C++14) Der \<chrono>-Header definiert zwölf [benutzerdefinierte Literale](../cpp/user-defined-literals-cpp.md), um die Nutzung von Literalen für Stunden, Minuten, Sekunden, Millisekunden, Mikrosekunden und Nanosekunden zu ermöglichen. Jedes benutzerdefinierte Literal verfügt über eine integrale und eine Gleitkommaüberladung. Die Literale werden im Inlinenamespace „literals::chrono_literals“ definiert, der automatisch im Bereich enthalten ist, wenn „std::chrono“ Teil des Bereichs ist.

## <a name="syntax"></a>Syntax

```cpp
inline namespace literals {
  inline namespace chrono_literals {
    // return integral hours
    constexpr chrono::hours operator"" h(unsigned long long Val);

    // return floating-point hours
    constexpr chrono::duration<double, ratio<3600>> operator"" h(long double Val);

    // return integral minutes
    constexpr chrono::minutes(operator"" min)(unsigned long long Val);

    // return floating-point minutes
    constexpr chrono::duration<double, ratio<60>>(operator"" min)(long double Val);

    // return integral seconds
    constexpr chrono::seconds operator"" s(unsigned long long Val);

    // return floating-point seconds
    constexpr chrono::duration<double> operator"" s(long double Val);

    // return integral milliseconds
    constexpr chrono::milliseconds operator"" ms(unsigned long long Val);

    // return floating-point milliseconds
    constexpr chrono::duration<double, milli> operator"" ms(long double Val);

    // return integral microseconds
    constexpr chrono::microseconds operator"" us(unsigned long long Val);

    // return floating-point microseconds
    inline constexpr chrono::duration<double, micro> operator"" us(long double Val);

    // return integral nanoseconds
    inline constexpr chrono::nanoseconds operator"" ns(unsigned long long Val);

    // return floating-point nanoseconds
    constexpr chrono::duration<double, nano> operator"" ns(long double Val);

  } // inline namespace chrono_literals
} // inline namespace literals
```

## <a name="return-value"></a>Rückgabewert

Die Literale, verwenden eine **long long** Rückgabe des Arguments, einen Wert oder einen entsprechenden Typ. Die Literale, die ein Gleitkommaargument verwenden, geben eine [Dauer](../standard-library/duration-class.md) zurück.

## <a name="example"></a>Beispiel

In den folgenden Beispielen wird die Verwendung von chrono-Literalen veranschaulicht.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="requirements"></a>Anforderungen

**Header**: \<chrono>

**Namespace**: std::literals::chrono_literals

## <a name="see-also"></a>Siehe auch

[\<chrono>](../standard-library/chrono.md)<br/>
