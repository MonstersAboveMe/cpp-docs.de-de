---
title: exponential_distribution-Klasse
ms.date: 11/04/2016
f1_keywords:
- random/std::exponential_distribution
- random/std::exponential_distribution::reset
- random/std::exponential_distribution::lambda
- random/std::exponential_distribution::param
- random/std::exponential_distribution::min
- random/std::exponential_distribution::max
- random/std::exponential_distribution::operator()
- random/std::exponential_distribution::param_type
- random/std::exponential_distribution::param_type::lambda
- random/std::exponential_distribution::param_type::operator==
- random/std::exponential_distribution::param_type::operator!=
helpviewer_keywords:
- std::exponential_distribution [C++]
- std::exponential_distribution [C++], reset
- std::exponential_distribution [C++], lambda
- std::exponential_distribution [C++], param
- std::exponential_distribution [C++], min
- std::exponential_distribution [C++], max
- std::exponential_distribution [C++], param_type
- std::exponential_distribution [C++], param_type
ms.assetid: d54f3126-a09b-45f9-a30b-0d94d03bcdc9
ms.openlocfilehash: a8dd8168075a0fff3b61154098c0bee100961f98
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451247"
---
# <a name="exponentialdistribution-class"></a>exponential_distribution-Klasse

Generiert eine exponentielle Verteilung.

## <a name="syntax"></a>Syntax

```cpp
template<class RealType = double>
class exponential_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructors and reset functions
   explicit exponential_distribution(result_type lambda = 1.0);
   explicit exponential_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type lambda() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parameter

*RealType*<br/>
Der gleitkommaergebnistyp standardmäßig **doppelte**. Mögliche Typen finden Sie unter [\<random>](../standard-library/random.md).

*URNG*<br/>
Die zufällige Zufallszahlengenerator-Engine. Mögliche Typen finden Sie unter [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Hinweise

Die Vorlagenklasse beschreibt eine Verteilung, Werte eines benutzerdefinierten ganzzahligen produziert, Typs **doppelte** Wenn none angegeben wird, entsprechend der exponentiellen Verteilung verteilter Wert. Die folgende Tabelle ist mit Artikeln über einzelne Member verknüpft.

||||
|-|-|-|
|[exponential_distribution](#exponential_distribution)|`exponential_distribution::lambda`|`exponential_distribution::param`|
|`exponential_distribution::operator()`||[param_type](#param_type)|

Die Eigenschaftenmember-Funktion `lambda()` gibt den Wert für den gespeicherten Verteilungsparameter `lambda` zurück.

Die Eigenschaftenmember-Funktion `param()` gibt das aktuell gespeicherte Verteilungspaket `param_type` zurück oder stellt es ein.

Weitere Informationen zu Verteilungsklassen und ihren Membern finden Sie unter [\<random>](../standard-library/random.md).

Ausführliche Informationen über die exponentielle Verteilung finden Sie im Wolfram MathWorld-Artikel [Exponential Distribution](https://go.microsoft.com/fwlink/p/?linkid=401098).

## <a name="example"></a>Beispiel

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double l, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;
    std::mt19937 gen(1701);

    std::exponential_distribution<> distr(l);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "lambda() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.lambda() << std::endl;

    // generate the distribution as a histogram
    std::map<double, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        std::cout << std::fixed << std::setw(11) << ++counter << ": "
            << std::setw(14) << std::setprecision(10) << elem.first << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double l_dist = 0.5;
    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the 'lambda' distribution parameter (must be greater than zero): ";
    std::cin >> l_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(l_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'lambda' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == 0
max() == 1.79769e+308
lambda() == 1.0000000000
Distribution for 10 samples:
    1: 0.0936880533
    2: 0.1225944894
    3: 0.6443593183
    4: 0.6551171649
    5: 0.7313457551
    6: 0.7313557977
    7: 0.7590097389
    8: 1.4466885214
    9: 1.6434088411
    10: 2.1201210996
```

## <a name="requirements"></a>Anforderungen

**Header:** \<random>

**Namespace:** std

## <a name="exponential_distribution"></a> exponential_distribution::exponential_distribution

Erstellt die Verteilung.

```cpp
explicit exponential_distribution(result_type lambda = 1.0);
explicit exponential_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parameter

*Lambda*<br/>
Der `lambda`-Verteilungsparameter.

*parm*<br/>
Das für die Erstellung der Verteilung verwendete Parameterpaket.

### <a name="remarks"></a>Hinweise

**Vorbedingung:** `0.0 < lambda`

Der erste Konstruktor konstruiert ein Objekt, dessen gespeicherter `lambda`-Wert den Wert *lambda* enthält.

Mit dem zweiten Konstruktor wird ein Objekt erstellt, dessen gespeicherte Parameter aus *parm* initialisiert werden. Sie können die aktuellen Parameter einer vorhandenen Verteilung abrufen und festlegen, indem Sie die Memberfunktion `param()` aufrufen.

## <a name="param_type"></a> exponential_distribution::param_type

Speichert die Parameter der Verteilung.

```cpp
struct param_type {
   typedef exponential_distribution<result_type> distribution_type;
   param_type(result_type lambda = 1.0);
   result_type lambda() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parameter

*Lambda*<br/>
Der `lambda`-Verteilungsparameter.

*right*<br/>
Das mit diesem `param_type`-Objekt zu vergleichende Objekt.

### <a name="remarks"></a>Hinweise

**Vorbedingung:** `0.0 < lambda`

Diese Struktur kann bei der Instanziierung an den Klassenkonstruktor des Verteilers, an die Memberfunktion `param()` (zur Festlegung der gespeicherten Parameter einer vorhandenen Verteilung) und an `operator()` (zur Verwendung anstelle der gespeicherten Parameter) übergeben werden.

## <a name="see-also"></a>Siehe auch

[\<random>](../standard-library/random.md)<br/>
