---
title: complex-Klasse
ms.date: 03/27/2019
f1_keywords:
- complex/std::complex::value_type
- complex/std::complex::imag
- complex/std::complex::real
helpviewer_keywords:
- std::complex [C++], value_type
- std::complex [C++], imag
- std::complex [C++], real
ms.assetid: d6492e1c-5eba-4bc5-835b-2a88001a5868
ms.openlocfilehash: 2ebaee81b792f9acc475fe25ac1ef7cc7a78a0de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376158"
---
# <a name="complex-class"></a>complex-Klasse

Die Vorlagenklasse beschreibt ein Objekt, das zwei Objekte vom Typ speichert `Type`, eines entspricht dem Realteil einer komplexen Zahl und eine, die den imaginären Teil darstellt.

## <a name="syntax"></a>Syntax

```cpp
template <class Type>
class complex
```

## <a name="remarks"></a>Hinweise

Ein Objekt der Klasse `Type`:

- Es hat einen öffentlichen Standardkonstruktor, Destruktor, Kopierkonstruktor und Zuweisungsoperator mit üblichem Verhalten.

- Ihm können ganzzahlige Werte oder Gleitkommawerte zugeordnet werden oder eine Typumwandlung zu diesen Werten mit üblichem Verhalten.

- Es definiert nach Bedarf die arithmetischen Operatoren und mathematischen Funktionen, die für die Gleitkommatypen definiert sind (mit üblichem Verhalten).

Insbesondere dürfen keine feinen Unterschiede zwischen einer Kopierkonstruktion und einer Standardkonstruktion bestehen, auf die eine Zuweisung folgt. Keiner der Vorgänge für Objekte der Klasse `Type` möglicherweise Ausnahmen auslösen.

Für die drei Gleitkommatypen sind explizite Spezialisierungen der Vorlagenklasse „complex“ vorhanden. In dieser Implementierung wird der Wert eines anderen Typs `Type` umgewandelt zu **doppelte** für tatsächliche Berechnungen, mit der **doppelte** Ergebnis zurück, die das gespeicherte Objekt vom Typ zugewiesen `Type`.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|Beschreibung|
|-|-|
|[complex](#complex)|Erstellt eine komplexe Zahl aus den angegebenen reellen und imaginären Teilen oder eine Kopie einer anderen komplexen Zahl.|

### <a name="typedefs"></a>Typedefs

|Typname|Beschreibung|
|-|-|
|[value_type](#value_type)|Ein Typ, der den Datentyp darstellt, der für die Darstellung der Real- und Imaginärteile einer komplexen Zahl verwendet wird|

### <a name="member-functions"></a>Memberfunktionen

|Member-Funktion|Beschreibung|
|-|-|
|[imag](#imag)|Extrahiert die imaginäre Komponente einer komplexen Zahl.|
|[real](#real)|Extrahiert die reelle Komponente einer komplexen Zahl.|

### <a name="operators"></a>Operatoren

|Operator|Beschreibung|
|-|-|
|[operator*=](#op_star_eq)|Multipliziert eine komplexe Zielzahl mit einem komplexen Faktor oder einem Faktor vom gleichen Typ wie die Real- und Imaginärteile der komplexen Zahl|
|[operator+=](#op_add_eq)|Fügt der komplexen Zielzahl eine Zahl hinzu, die komplex ist oder vom gleichen Typ wie die Real- und Imaginärteile der komplexen Zahl, der sie hinzugefügt wird|
|[operator-=](#operator-_eq)|Subtrahiert eine Zahl von der komplexen Zielzahl, wobei die subtrahiert Zahl komplex ist oder vom gleichen Typ wie die Real- und Imaginärteile der komplexen Zahl, von der sie subtrahiert wurde|
|[operator/=](#op_div_eq)|Dividiert eine komplexe Zielzahl durch einen komplexen Faktor oder einen Faktor vom gleichen Typ wie die Real- und Imaginärteile der komplexen Zahl|
|[operator=](#op_eq)|Weist der komplexen Zielzahl eine Zahl hinzu, die komplex ist oder vom gleichen Typ wie die Real- und Imaginärteile der komplexen Zahl, der sie hinzugefügt wird|

## <a name="requirements"></a>Anforderungen

**Header**: \<complex>

**Namespace:** std

## <a name="complex"></a>  complex::complex

Erstellt eine komplexe Zahl aus den angegebenen reellen und imaginären Teilen oder eine Kopie einer anderen komplexen Zahl.

```cpp
constexpr complex(
    const T& _RealVal = 0,
    const T& _ImagVal = 0);

template <class Other>
constexpr complex(
    const complex<Other>& complexNum);
```

### <a name="parameters"></a>Parameter

*_RealVal*<br/>
Der Wert des reellen Teils, der zum Initialisieren der zu erstellenden komplexen Zahl verwendet wird.

*_ImagVal*<br/>
Der Wert des imaginären Teils, der zum Initialisieren der zu erstellenden komplexen Zahl verwendet wird.

*complexNum*<br/>
Die komplexe Zahl, deren reelle und imaginäre Teile zum Initialisieren der zu erstellenden komplexen Zahl verwendet werden.

### <a name="remarks"></a>Hinweise

Der erste Konstruktor initialisiert den gespeicherten reellen Teil in  *\_RealVal* und den gespeicherten imaginären Teil in  *\_Imagval*. Der zweite Konstruktor initialisiert den gespeicherten reellen Teil in `complexNum.real()` und den gespeicherten imaginären Teil in `complexNum.imag()`.

In dieser Implementierung wird, falls ein Konvertierungsprogramm Memberfunktionen der Vorlage nicht unterstützt, die Vorlage:

```cpp
template <class Other>
complex(const complex<Other>& right);
```

durch Folgendes ersetzt:

```
complex(const complex& right);
```

Hierbei handelt es sich um den Kopierkonstruktor.

### <a name="example"></a>Beispiel

```cpp
// complex_complex.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    double pi = 3.14159265359;

    // The first constructor specifies real & imaginary parts
    complex<double> c1( 4.0 , 5.0 );
    cout << "Specifying initial real & imaginary parts,"
        << "c1 = " << c1 << endl;

    // The second constructor initializes values of the real &
    // imaginary parts using those of another complex number
    complex<double> c2( c1 );
    cout << "Initializing with the real and imaginary parts of c1,"
        << " c2 = " << c2 << endl;

    // Complex numbers can be initialized in polar form
    // but will be stored in Cartesian form
    complex<double> c3( polar( sqrt( (double)8 ) , pi / 4 ) );
    cout << "c3 = polar( sqrt( 8 ) , pi / 4 ) = " << c3 << endl;

    // The modulus and argument of a complex number can be recovered
    double absc3 = abs( c3 );
    double argc3 = arg( c3 );
    cout << "The modulus of c3 is recovered from c3 using: abs( c3 ) = "
        << absc3 << endl;
    cout << "Argument of c3 is recovered from c3 using:\n arg( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

## <a name="imag"></a>  complex::imag

Extrahiert die imaginäre Komponente einer komplexen Zahl.

```cpp
T imag() const;

T imag(const T& right);
```

### <a name="parameters"></a>Parameter

*right*<br/>
Eine komplexe Zahl, deren imaginärer Wert extrahiert werden soll.

### <a name="return-value"></a>Rückgabewert

Der imaginäre Teil der komplexen Zahl.

### <a name="remarks"></a>Hinweise

Für eine komplexe Zahl *a + Bi*, ist der imaginäre Teil bzw. Komponente *Im(a + bi) = b*.

### <a name="example"></a>Beispiel

```cpp
// complex_imag.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;

    complex<double> c1( 4.0 , 3.0 );
    cout << "The complex number c1 = " << c1 << endl;

    double dr1 = c1.real();
    cout << "The real part of c1 is c1.real() = "
        << dr1 << "." << endl;

    double di1 = c1.imag();
    cout << "The imaginary part of c1 is c1.imag() = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real() = 4.
The imaginary part of c1 is c1.imag() = 3.
```

## <a name="op_star_eq"></a> complex::operator*=

Multipliziert eine komplexe Zielzahl mit einem komplexen Faktor oder einem Faktor vom gleichen Typ wie die Real- und Imaginärteile der komplexen Zahl

```cpp
template <class Other>
complex& operator*=(const complex<Other>& right);

complex<Type>& operator*=(const Type& right);

complex<Type>& operator*=(const complex<Type>& right);
```

### <a name="parameters"></a>Parameter

*right*<br/>
Eine komplexe Zahl oder eine Zahl vom gleichen Typ wie der Parameter der komplexen Zielzahl

### <a name="return-value"></a>Rückgabewert

Eine komplexe Zahl, die mit der als Parameter angegebenen Zahl multipliziert wurde

### <a name="remarks"></a>Hinweise

Die Operation wird überladen, damit einfache arithmetische Operationen ohne Konvertierung der Daten in ein bestimmtes Format ausgeführt werden können.

### <a name="example"></a>Beispiel

```cpp
// complex_op_me.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main()
{
    using namespace std;
    double pi = 3.14159265359;

    // Example of the first member function
    // type complex<double> multiplied by type complex<double>
    complex<double> cl1( polar ( 3.0 , pi / 6 ) );
    complex<double> cr1( polar ( 2.0 , pi / 3 ) );
    cout << "The left-side complex number is cl1 = " << cl1 << endl;
    cout << "The right-side complex number is cr1 = " << cr1 << endl;

    complex<double> cs1 = cl1 * cr1;
    cout << "Quotient of two complex numbers is: cs1 = cl1 * cr1 = "
        << cs1 << endl;

    // This is equivalent to the following operation
    cl1 *= cr1;
    cout << "Quotient of two complex numbers is also: cl1 *= cr1 = "
        << cl1 << endl;

    double abscl1 = abs ( cl1 );
    double argcl1 = arg ( cl1 );
    cout << "The modulus of cl1 is: " << abscl1 << endl;
    cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

    // Example of the second member function
    // type complex<double> multiplied by type double
    complex<double> cl2 ( polar ( 3.0 , pi / 6 ) );
    double cr2 = 5.0;
    cout << "The left-side complex number is cl2 = " << cl2 << endl;
    cout << "The right-side complex number is cr2 = " << cr2 << endl;

    complex<double> cs2 = cl2 * cr2;
    cout << "Quotient of two complex numbers is: cs2 = cl2 * cr2 = "
        << cs2 << endl;

    // This is equivalent to the following operation
    cl2 *= cr2;
    cout << "Quotient of two complex numbers is also: cl2 *= cr2 = "
        << cl2 << endl;

    double abscl2 = abs ( cl2 );
    double argcl2 = arg ( cl2 );
    cout << "The modulus of cl2 is: " << abscl2 << endl;
    cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl;
}
```

## <a name="op_add_eq"></a>  complex::operator+=

Fügt der komplexen Zielzahl eine Zahl hinzu, die komplex ist oder vom gleichen Typ wie die Real- und Imaginärteile der komplexen Zahl, der sie hinzugefügt wird

```cpp
template <class Other>
complex<Type>& operator+=(const complex<Other>& right);

complex<Type>& operator+=(const Type& right);

complex<Type>& operator+=(const complex<Type>& right);
```

### <a name="parameters"></a>Parameter

*right*<br/>
Eine komplexe Zahl oder eine Zahl vom gleichen Typ wie der Parameter der komplexen Zielzahl

### <a name="return-value"></a>Rückgabewert

Eine komplexe Zahl, der die als Parameter angegebene Zahl hinzugefügt wurde

### <a name="remarks"></a>Hinweise

Die Operation wird überladen, damit einfache arithmetische Operationen ohne Konvertierung der Daten in ein bestimmtes Format ausgeführt werden können.

### <a name="example"></a>Beispiel

```cpp
// complex_op_pe.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> added to type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 + cr1;
   cout << "The sum of the two complex numbers is: cs1 = cl1 + cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 += cr1;
   cout << "The complex number cr1 added to the complex number cl1 is:"
        << "\n cl1 += cr1 = " << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double added to type complex<double>
   complex<double> cl2( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 + cr2;
   cout << "The sum of the two complex numbers is: cs2 = cl2 + cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 += cr2;
   cout << "The complex number cr2 added to the complex number cl2 is:"
        << "\n cl2 += cr2 = " << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The sum of the two complex numbers is: cs1 = cl1 + cr1 = (5,3)
The complex number cr1 added to the complex number cl1 is:
cl1 += cr1 = (5,3)
The modulus of cl1 is: 5.83095
The argument of cl1 is: 0.54042 radians, which is 30.9638 degrees.

The left-side complex number is cl2 = (-2,4)
The right-side complex number is cr2 = 5
The sum of the two complex numbers is: cs2 = cl2 + cr2 = (3,4)
The complex number cr2 added to the complex number cl2 is:
cl2 += cr2 = (3,4)
The modulus of cl2 is: 5
The argument of cl2 is: 0.927295 radians, which is 53.1301 degrees.
```

## <a name="operator-_eq">complex::operator-=</a>

Subtrahiert eine Zahl von der komplexen Zielzahl, wobei die subtrahiert Zahl komplex ist oder vom gleichen Typ wie die Real- und Imaginärteile der komplexen Zahl, von der sie subtrahiert wurde

```cpp
template <class Other>
complex<Type>& operator-=(const complex<Other>& complexNum);

complex<Type>& operator-=(const Type& _RealPart);

complex<Type>& operator-=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>Parameter

*complexNum*<br/>
Eine komplexe Zahl, die von der komplexen Zielzahl subtrahiert werden soll

*_RealPart*<br/>
Eine reelle Zahl, die von der komplexen Zielzahl subtrahiert werden soll

### <a name="return-value"></a>Rückgabewert

Eine komplexe Zahl, von der die als Parameter angegebene Zahl subtrahiert wurde

### <a name="remarks"></a>Hinweise

Die Operation wird überladen, damit einfache arithmetische Operationen ohne Konvertierung der Daten in ein bestimmtes Format ausgeführt werden können.

### <a name="example"></a>Beispiel

```cpp
// complex_op_se.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> subtracted from type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 - cr1;
   cout << "The difference between the two complex numbers is:"
        << "\n cs1 = cl1 - cr1 = " << cs1 << endl;

   // This is equivalent to the following operation
   cl1 -= cr1;
   cout << "Complex number cr1 subtracted from complex number cl1 is:"
        << "\n cl1 -= cr1 = " << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double subtracted from type complex<double>
   complex<double> cl2( 2.0 , 4.0 );
   double cr2 = 5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 - cr2;
   cout << "The difference between the two complex numbers is:"
        << "\n cs2 = cl2 - cr2 = " << cs2 << endl;

   // This is equivalent to the following operation
   cl2  -= cr2;
   cout << "Complex number cr2 subtracted from complex number cl2 is:"
        << "\n cl2 -= cr2 = " << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The difference between the two complex numbers is:
cs1 = cl1 - cr1 = (1,5)
Complex number cr1 subtracted from complex number cl1 is:
cl1 -= cr1 = (1,5)
The modulus of cl1 is: 5.09902
The argument of cl1 is: 1.3734 radians, which is 78.6901 degrees.

The left-side complex number is cl2 = (2,4)
The right-side complex number is cr2 = 5
The difference between the two complex numbers is:
cs2 = cl2 - cr2 = (-3,4)
Complex number cr2 subtracted from complex number cl2 is:
cl2 -= cr2 = (-3,4)
The modulus of cl2 is: 5
The argument of cl2 is: 2.2143 radians, which is 126.87 degrees.
```

## <a name="op_div_eq"></a>  complex::operator/=

Dividiert eine komplexe Zielzahl durch einen komplexen Faktor oder einen Faktor vom gleichen Typ wie die Real- und Imaginärteile der komplexen Zahl

```cpp
template <class Other>
complex<Type>& operator/=(const complex<Other>& complexNum);

complex<Type>& operator/=(const Type& _RealPart);

complex<Type>& operator/=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>Parameter

*complexNum*<br/>
Eine komplexe Zahl, die von der komplexen Zielzahl subtrahiert werden soll

*_RealPart*<br/>
Eine reelle Zahl, die von der komplexen Zielzahl subtrahiert werden soll

### <a name="return-value"></a>Rückgabewert

Eine komplexe Zahl, die durch die als Parameter angegebene Zahl dividiert wurde

### <a name="remarks"></a>Hinweise

Die Operation wird überladen, damit einfache arithmetische Operationen ohne Konvertierung der Daten in ein bestimmtes Format ausgeführt werden können.

### <a name="example"></a>Beispiel

```cpp
// complex_op_de.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> divided by type complex<double>
   complex<double> cl1( polar (3.0 , pi / 6 ) );
   complex<double> cr1( polar (2.0 , pi / 3 ) );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 / cr1;
   cout << "The quotient of the two complex numbers is: cs1 = cl1 /cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 /= cr1;
   cout << "Quotient of two complex numbers is also: cl1 /= cr1 = "
        << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type complex<double> divided by type double
   complex<double> cl2( polar(3.0 , pi / 6 ) );
   double cr2 =5;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 / cr2;
   cout << "The quotient of the two complex numbers is: cs2 /= cl2 cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 /= cr2;
   cout << "Quotient of two complex numbers is also: cl2 = /cr2 = "
        << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (2.59808,1.5)
The right-side complex number is cr1 = (1,1.73205)
The quotient of the two complex numbers is: cs1 = cl1 /cr1 = (1.29904,-0.75)
Quotient of two complex numbers is also: cl1 /= cr1 = (1.29904,-0.75)
The modulus of cl1 is: 1.5
The argument of cl1 is: -0.523599 radians, which is -30 degrees.

The left-side complex number is cl2 = (2.59808,1.5)
The right-side complex number is cr2 = 5
The quotient of the two complex numbers is: cs2 /= cl2 cr2 = (0.519615,0.3)
Quotient of two complex numbers is also: cl2 = /cr2 = (0.519615,0.3)
The modulus of cl2 is: 0.6
The argument of cl2 is: 0.523599 radians, which is 30 degrees.
```

## <a name="op_eq"></a> complex::operator=

Weist der komplexen Zielzahl eine Zahl hinzu, die komplex ist oder vom gleichen Typ wie die Real- und Imaginärteile der komplexen Zahl, der sie hinzugefügt wird

```cpp
template <class Other>
complex<Type>& operator=(const complex<Other>& right);

complex<Type>& operator=(const Type& right);
```

### <a name="parameters"></a>Parameter

*right*<br/>
Eine komplexe Zahl oder eine Zahl vom gleichen Typ wie der Parameter der komplexen Zielzahl

### <a name="return-value"></a>Rückgabewert

Eine komplexe Zahl, der die als Parameter angegebene Zahl zugewiesen wurde

### <a name="remarks"></a>Hinweise

Die Operation wird überladen, damit einfache arithmetische Operationen ohne Konvertierung der Daten in ein bestimmtes Format ausgeführt werden können.

### <a name="example"></a>Beispiel

```cpp
// complex_op_as.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> assigned to type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   cl1  = cr1;
   cout << "The complex number cr1 assigned to the complex number cl1 is:"
        << "\ncl1 = cr1 = " << cl1 << endl;

   // Example of the second member function
   // type double assigned to type complex<double>
   complex<double> cl2( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   cl2 = cr2;
   cout << "The complex number cr2 assigned to the complex number cl2 is:"
        << "\ncl2 = cr2 = " << cl2 << endl;

   cl2 = complex<double>(3.0, 4.0);
   cout << "The complex number (3, 4) assigned to the complex number cl2 is:"
        << "\ncl2 = " << cl2 << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The complex number cr1 assigned to the complex number cl1 is:
cl1 = cr1 = (2,-1)
The left-side complex number is cl2 = (-2,4)
The right-side complex number is cr2 = 5
The complex number cr2 assigned to the complex number cl2 is:
cl2 = cr2 = (5,0)
The complex number (3, 4) assigned to the complex number cl2 is:
cl2 = (3,4)
```

## <a name="real"></a> complex::real

Ruft die reelle Komponente einer komplexen Zahl ab, oder legt diese fest.

```cpp
constexpr T real() const;

T real(const T& right);
```

### <a name="parameters"></a>Parameter

*right*<br/>
Eine komplexe Zahl, deren reeller Wert extrahiert werden soll.

### <a name="return-value"></a>Rückgabewert

Der reelle Teil der komplexen Zahl.

### <a name="remarks"></a>Hinweise

Für eine komplexe Zahl *a + Bi*, ist der reelle Teil bzw. Komponente *Re(a + BI) = eine*.

### <a name="example"></a>Beispiel

```cpp
// complex_class_real.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;

   complex<double> c1( 4.0 , 3.0 );
   cout << "The complex number c1 = " << c1 << endl;

   double dr1 = c1.real();
   cout << "The real part of c1 is c1.real() = "
        << dr1 << "." << endl;

   double di1 = c1.imag();
   cout << "The imaginary part of c1 is c1.imag() = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real() = 4.
The imaginary part of c1 is c1.imag() = 3.
```

## <a name="value_type"></a> complex::value_type

Ein Typ, der den Datentyp darstellt, der für die Darstellung der Real- und Imaginärteile einer komplexen Zahl verwendet wird

```
typedef Type value_type;
```

### <a name="remarks"></a>Hinweise

`value_type` ist ein Synonym für die Klasse komplexen `Type` Template-Parameter.

### <a name="example"></a>Beispiel

```cpp
// complex_valuetype.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    complex<double>::value_type a = 3, b = 4;

    complex<double> c1 ( a , b );
    cout << "Specifying initial real & imaginary parts"
        << "\nof type value_type: "
        << "c1 = " << c1 << "." << endl;
}
```

```Output
Specifying initial real & imaginary parts
of type value_type: c1 = (3,4).
```

## <a name="see-also"></a>Siehe auch

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
