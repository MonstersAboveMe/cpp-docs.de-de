---
title: regex_traits-Klasse
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_traits
- regex/std::regex_traits::char_type
- regex/std::regex_traits::size_type
- regex/std::regex_traits::string_type
- regex/std::regex_traits::locale_type
- regex/std::regex_traits::char_class_type
- regex/std::regex_traits::length
- regex/std::regex_traits::translate
- regex/std::regex_traits::translate_nocase
- regex/std::regex_traits::transform
- regex/std::regex_traits::transform_primary
- regex/std::regex_traits::lookup_classname
- regex/std::regex_traits::lookup_collatename
- regex/std::regex_traits::isctype
- regex/std::regex_traits::value
- regex/std::regex_traits::imbue
- regex/std::regex_traits::getloc
helpviewer_keywords:
- std::regex_traits [C++]
- std::regex_traits [C++], char_type
- std::regex_traits [C++], size_type
- std::regex_traits [C++], string_type
- std::regex_traits [C++], locale_type
- std::regex_traits [C++], char_class_type
- std::regex_traits [C++], length
- std::regex_traits [C++], translate
- std::regex_traits [C++], translate_nocase
- std::regex_traits [C++], transform
- std::regex_traits [C++], transform_primary
- std::regex_traits [C++], lookup_classname
- std::regex_traits [C++], lookup_collatename
- std::regex_traits [C++], isctype
- std::regex_traits [C++], value
- std::regex_traits [C++], imbue
- std::regex_traits [C++], getloc
ms.assetid: bc5a5eed-32fc-4eb7-913d-71c42e729e81
ms.openlocfilehash: 47e0a1e51809efad2924a2051d1627fe2e9ff95f
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400679"
---
# <a name="regextraits-class"></a>regex_traits-Klasse

Beschreibt die Merkmale von Elementen zum Abgleichen.

## <a name="syntax"></a>Syntax

```cpp
template<class Elem>
class regex_traits
```

## <a name="parameters"></a>Parameter

*Elem*<br/>
Der zu beschreibende Zeichenfolgentyp.

## <a name="remarks"></a>Hinweise

Die Vorlagenklasse beschreibt verschiedene Merkmale des regulären Ausdrucks für den Typ *Elem*. Die Vorlagenklasse [Basic_regex-Klasse](../standard-library/basic-regex-class.md) verwendet diese Informationen zum Bearbeiten von Elementen des Typs *Elem*.

Jedes `regex_traits` -Objekt enthält ein Objekt des Typs `regex_traits::locale` , das von einigen seiner Memberfunktionen verwendet wird. Das Standardgebietsschema ist eine Kopie von `regex_traits::locale()`. Die Memberfunktion `imbue` ersetzt das lokale Objekt, und die `getloc` -Memberfunktion gibt eine Kopie des Gebietsschemaobjekts zurück.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|Beschreibung|
|-|-|
|[regex_traits](#regex_traits)|Erstellt das Objekt.|

### <a name="typedefs"></a>Typedefs

|Typname|Beschreibung|
|-|-|
|[char_class_type](#char_class_type)|Der Typ der Zeichenklassenkennzeichner.|
|[char_type](#char_type)|Der Typ eines Elements.|
|[locale_type](#locale_type)|Der Typ des gespeicherten Gebietsschemaobjekts.|
|[size_type](#size_type)|Der Typ der Sequenzlänge.|
|[string_type](#string_type)|Der Typ einer Zeichenfolge von Elementen.|

### <a name="member-functions"></a>Memberfunktionen

|Member-Funktion|Beschreibung|
|-|-|
|[getloc](#getloc)|Gibt das gespeicherte Gebietsschemaobjekt zurück.|
|[imbue](#imbue)|Ändert das gespeicherte Gebietsschemaobjekt.|
|[isctype](#isctype)|Führt einen Test hinsichtlich der Mitgliedschaft durch.|
|[length](#length)|Die Länge einer Null endende Sequenz zurückgegeben.|
|[lookup_classname](#lookup_classname)|Ordnet eine Sequenz einer Zeichenklasse zu.|
|[lookup_collatename](#lookup_collatename)|Ordnet eine Sequenz einem Sortierungselement zu.|
|[transform](#transform)|Konvertiert in eine äquivalente sortierte Sequenz.|
|[transform_primary](#transform_primary)|Konvertiert in eine äquivalente fallunabhängig sortierte Sequenz.|
|[translate](#translate)|Konvertiert in ein äquivalentes übereinstimmendes Element.|
|[translate_nocase](#translate_nocase)|Konvertiert in ein äquivalentes fallunabhängiges übereinstimmendes Element.|
|[value](#value)|Konvertiert ein Element in einen Ziffernwert.|

## <a name="requirements"></a>Anforderungen

**Header:** \<regex >

**Namespace:** std

## <a name="example"></a>Beispiel

```cpp
// std__regex__regex_traits.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::regex_traits<char> Mytr;
int main()
    {
    Mytr tr;

    Mytr::char_type ch = tr.translate('a');
    std::cout << "translate('a') == 'a' == " << std::boolalpha
        << (ch == 'a') << std::endl;

    std::cout << "nocase 'a' == 'A' == " << std::boolalpha
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))
        << std::endl;

    const char *lbegin = "abc";
    const char *lend = lbegin + strlen(lbegin);
    Mytr::size_type size = tr.length(lbegin);
    std::cout << "length(\"abc\") == " << size <<std::endl;

    Mytr::string_type str = tr.transform(lbegin, lend);
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha
        << (str < "abc") << std::endl;

    const char *ubegin = "ABC";
    const char *uend = ubegin + strlen(ubegin);
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha
        << (tr.transform_primary(ubegin, uend) <
            tr.transform_primary(lbegin, lend))
        << std::endl;

    const char *dig = "digit";
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);
    std::cout << "class digit == d == " << std::boolalpha
        << (cl == tr.lookup_classname(dig, dig + 1))
        << std::endl;

    std::cout << "'3' is digit == " <<std::boolalpha
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))
        << std::endl;

    std::cout << "hex C == " << tr.value('C', 16) << std::endl;

// other members
    str = tr.lookup_collatename(dig, dig + 5);

    Mytr::locale_type loc = tr.getloc();
    tr.imbue(loc);

    return (0);
    }
```

```Output
translate('a') == 'a' == true
nocase 'a' == 'A' == true
length("abc") == 3
transform("abc") < "abc" == false
primary "ABC" < "abc" == false
class digit == d == true
'3' is digit == true
hex C == 12
```

## <a name="char_class_type"></a> regex_traits::char_class_type

Der Typ der Zeichenklassenkennzeichner.

```cpp
typedef T8 char_class_type;
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Synonym für einen nicht angegebenen Typ, der Zeichenklassen bestimmt. Werte dieses Typs können über den `|` -Operator kombiniert werden, um Zeichenklassen zu bestimmen, die die Vereinigung der Klassen sind, die von den Operanden bestimmt sind.

## <a name="char_type"></a> regex_traits::char_type

Der Typ eines Elements.

```cpp
typedef Elem char_type;
```

### <a name="remarks"></a>Hinweise

Die Typedef stellt ein Synonym für das Vorlagenargument `Elem`dar.

## <a name="getloc"></a> regex_traits::getloc

Gibt das gespeicherte Gebietsschemaobjekt zurück.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt das gespeicherte `locale` -Objekt zurück.

## <a name="imbue"></a> regex_traits::imbue

Ändert das gespeicherte Gebietsschemaobjekt.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parameter

*loc*<br/>
Das zu speichernde Gebietsschemaobjekt.

### <a name="remarks"></a>Hinweise

Die Memberfunktion kopiert *Loc* gespeicherten `locale` Objekt und gibt eine Kopie des vorherigen Werts des gespeicherten `locale` Objekt.

## <a name="isctype"></a> regex_traits::isctype

Führt einen Test hinsichtlich der Mitgliedschaft durch.

```cpp
bool isctype(char_type ch, char_class_type cls) const;
```

### <a name="parameters"></a>Parameter

*ch*<br/>
Das zu testende Element.

*cls*<br/>
Die Klassen, für die der Test ausgeführt wird.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt "true" zurück, wenn nur das Zeichen *ch* befindet sich in der vom angegebenen Zeichenklasse *Cls*.

## <a name="length"></a> regex_traits::length

Die Länge einer Null endende Sequenz zurückgegeben.

```cpp
static size_type length(const char_type *str);
```

### <a name="parameters"></a>Parameter

*str*<br/>
Die nullterminierte Sequenz.

### <a name="remarks"></a>Hinweise

Die statische Memberfunktion gibt `std::char_traits<char_type>::length(str)`zurück.

## <a name="locale_type"></a> regex_traits::locale_type

Der Typ des gespeicherten Gebietsschemaobjekts.

```cpp
typedef T7 locale_type;
```

### <a name="remarks"></a>Hinweise

Die Typedef ist ein Synonym für einen Typ, der Gebietsschemas kapselt. In den Spezialisierungen `regex_traits<char>` und `regex_traits<wchar_t>` ist die Typdefinition ein Synonym für `std::locale`.

## <a name="lookup_classname"></a> regex_traits::lookup_classname

Ordnet eine Sequenz einer Zeichenklasse zu.

```cpp
template <class FwdIt>
char_class_type lookup_classname(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Anfang der Sequenz, die gesucht werden soll.

*last*<br/>
Ende der Sequenz, die gesucht werden soll.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt einen Wert zurück, der die Zeichenklasse bestimmt, die von der Zeichenfolgensequenz benannt wird, auf die ihre Argumente zeigen. Der Wert ist nicht von der Groß-/Kleinschreibung der Zeichen in der Sequenz abhängig.

Die Spezialisierung `regex_traits<char>` erkennt die Namen `"d"`, `"s"`, `"w"`, `"alnum"`, `"alpha"`, `"blank"`, `"cntrl"`, `"digit"`, `"graph"`, `"lower"`, `"print"`, `"punct"`, `"space"`, `"upper"` und `"xdigit"`, alle unabhängig von der Groß-/Kleinschreibung.

Die Spezialisierung `regex_traits<wchar_t>` erkennt die Namen `L"d"`, `L"s"`, `L"w"`, `L"alnum"`, `L"alpha"`, `L"blank"`, `L"cntrl"`, `L"digit"`, `L"graph"`, `L"lower"`, `L"print"`, `L"punct"`, `L"space"`, `L"upper"` und `L"xdigit"`, alle unabhängig von der Groß-/Kleinschreibung.

## <a name="lookup_collatename"></a> regex_traits::lookup_collatename

Ordnet eine Sequenz einem Sortierungselement zu.

```cpp
template <class FwdIt>
string_type lookup_collatename(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Anfang der Sequenz, die gesucht werden soll.

*last*<br/>
Ende der Sequenz, die gesucht werden soll.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt ein String-Objekt zurück, das das Sortierungselement enthält, das der Sequenz `[first, last)`entspricht, oder gibt eine leere Zeichenfolge zurück, wenn die Sequenz kein gültiges Sortierungselement ist.

## <a name="regex_traits"></a> regex_traits::regex_traits

Erstellt das Objekt.

```cpp
regex_traits();
```

### <a name="remarks"></a>Hinweise

Mit dem Konstruktor wird ein Objekt erstellt, dessen gespeichertes `locale`-Objekt mit dem Standardgebietsschema initialisiert wird.

## <a name="size_type"></a> regex_traits::size_type

Der Typ der Sequenzlänge.

```cpp
typedef T6 size_type;
```

### <a name="remarks"></a>Hinweise

Die Typdefinition (typedef) ist ein Synonym für einen ganzzahligen Typ ohne Vorzeichen. In den Spezialisierungen `regex_traits<char>` und `regex_traits<wchar_t>` ist die Typdefinition ein Synonym für `std::size_t`.

Die Typedef ist ein Synonym für `std::size_t`.

## <a name="string_type"></a> regex_traits::string_type

Der Typ einer Zeichenfolge von Elementen.

```cpp
typedef basic_string<Elem> string_type;
```

### <a name="remarks"></a>Hinweise

Die Typedef ist ein Synonym für `basic_string<Elem>`.

## <a name="transform"></a> regex_traits::transform

Konvertiert in eine äquivalente sortierte Sequenz.

```cpp
template <class FwdIt>
string_type transform(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Der Anfang der umzuwandelnden Sequenz.

*last*<br/>
Das Ende der umzuwandelnden Sequenz.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt eine Zeichenfolge zurück, die sie mithilfe einer Transformationsregel generiert, die von dem gespeicherten `locale` -Objekt abhängig ist. Für zwei Zeichenfolgen, die durch die Iteratorbereiche `[first1, last1)` und `[first2, last2)`bestimmt sind. `transform(first1, last1) < transform(first2, last2)` , wenn die durch den Iteratorbereich `[first1, last1)` bezeichnete Zeichenfolge vor der durch den Interatorbereich `[first2, last2)`bezeichneten Zeichenfolge sortiert wird.

## <a name="transform_primary"></a> regex_traits::transform_primary

Konvertiert in eine äquivalente fallunabhängig sortierte Sequenz.

```cpp
template <class FwdIt>
string_type transform_primary(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Der Anfang der umzuwandelnden Sequenz.

*last*<br/>
Das Ende der umzuwandelnden Sequenz.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt eine Zeichenfolge zurück, die sie mithilfe einer Transformationsregel generiert, die von dem gespeicherten `locale` -Objekt abhängig ist. Für zwei Zeichenfolgen, die durch die Iteratorbereiche `[first1, last1)` und `[first2, last2)`bestimmt sind. `transform_primary(first1, last1) < transform_primary(first2, last2)` , wenn die durch den Iteratorbereich `[first1, last1)` bezeichnete Zeichenfolge vor der durch den Iteratorbereich `[first2, last2)` bezeichneten Zeichenfolge ohne Berücksichtigung der Groß-/Kleinschreibung oder von Akzenten sortiert wird.

## <a name="translate"></a> regex_traits::translate

Konvertiert in ein äquivalentes übereinstimmendes Element.

```cpp
char_type translate(char_type ch) const;
```

### <a name="parameters"></a>Parameter

*ch*<br/>
Das zu konvertierende Element.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt ein Zeichen zurück, das sie mithilfe einer Transformationsregel generiert, die von dem gespeicherten `locale` -Objekt abhängig ist. Für zwei `char_type` -Objekte `ch1` und `ch2`, `translate(ch1) == translate(ch2)` nur, wenn `ch1` und `ch2` übereinstimmen, wenn ein Element in der Definition des regulären Ausdrucks und das andere an der entsprechenden Position in der Zielsequenz für eine Übereinstimmung unter Beachtung des Gebietsschemas auftritt.

## <a name="translate_nocase"></a> regex_traits::translate_nocase

Konvertiert in ein äquivalentes fallunabhängiges übereinstimmendes Element.

```cpp
char_type translate_nocase(char_type ch) const;
```

### <a name="parameters"></a>Parameter

*ch*<br/>
Das zu konvertierende Element.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt ein Zeichen zurück, das sie mithilfe einer Transformationsregel generiert, die von dem gespeicherten `locale` -Objekt abhängig ist. Für zwei `char_type` -Objekte `ch1` und `ch2`, `translate_nocase(ch1) == translate_nocase(ch2)` nur, wenn `ch1` und `ch2` übereinstimmen, wenn ein Element in der Definition des regulären Ausdrucks und das andere an der entsprechenden Position in der Zielsequenz für eine Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung auftritt.

## <a name="value"></a> regex_traits::value

Konvertiert ein Element in einen Ziffernwert.

```cpp
int value(Elem ch, int radix) const;
```

### <a name="parameters"></a>Parameter

*ch*<br/>
Das zu konvertierende Element.

*radix*<br/>
Die zu verwendende arithmetische Basis.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt den Wert, der durch das Zeichen dargestellt *ch* in der Basisklasse *Basis*, oder -1, wenn *ch* ist keine gültige Ziffer in der Basisklasse *Basis*. Die Funktion wird nur aufgerufen werden, mit einem *Basis* Argument von 8, 10 oder 16.

## <a name="see-also"></a>Siehe auch

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants-Klasse](../standard-library/regex-constants-class.md)<br/>
[regex_error-Klasse](../standard-library/regex-error-class.md)<br/>
[\<regex>-Funktionen](../standard-library/regex-functions.md)<br/>
[regex_iterator-Klasse](../standard-library/regex-iterator-class.md)<br/>
[\<regex>-Operatoren](../standard-library/regex-operators.md)<br/>
[regex_token_iterator-Klasse](../standard-library/regex-token-iterator-class.md)<br/>
[\<regex>-Typdefinitionen](../standard-library/regex-typedefs.md)<br/>
[Regex_traits\<Char >-Klasse](../standard-library/regex-traits-char-class.md)<br/>
[regex_traits\<wchar_t>-Klasse](../standard-library/regex-traits-wchar-t-class.md)<br/>
