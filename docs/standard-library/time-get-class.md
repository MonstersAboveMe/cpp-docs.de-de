---
title: time_get-Klasse
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get
- locale/std::time_get::char_type
- locale/std::time_get::iter_type
- locale/std::time_get::date_order
- locale/std::time_get::do_date_order
- locale/std::time_get::do_get
- locale/std::time_get::do_get_date
- locale/std::time_get::do_get_monthname
- locale/std::time_get::do_get_time
- locale/std::time_get::do_get_weekday
- locale/std::time_get::do_get_year
- locale/std::time_get::get
- locale/std::time_get::get_date
- locale/std::time_get::get_monthname
- locale/std::time_get::get_time
- locale/std::time_get::get_weekday
- locale/std::time_get::get_year
helpviewer_keywords:
- std::time_get [C++]
- std::time_get [C++], char_type
- std::time_get [C++], iter_type
- std::time_get [C++], date_order
- std::time_get [C++], do_date_order
- std::time_get [C++], do_get
- std::time_get [C++], do_get_date
- std::time_get [C++], do_get_monthname
- std::time_get [C++], do_get_time
- std::time_get [C++], do_get_weekday
- std::time_get [C++], do_get_year
- std::time_get [C++], get
- std::time_get [C++], get_date
- std::time_get [C++], get_monthname
- std::time_get [C++], get_time
- std::time_get [C++], get_weekday
- std::time_get [C++], get_year
ms.assetid: 869d5f5b-dbab-4628-8333-bdea7e272023
ms.openlocfilehash: df5a6da3995b1485585a3105ac027f19a27dc8eb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412032"
---
# <a name="timeget-class"></a>time_get-Klasse

Die Vorlagenklasse, die ein Objekt beschreibt, das als Gebietsschemafacet dienen kann, um Konvertierungen von Sequenzen des Typs `CharType` in Zeitwerte zu steuern.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>Parameter

*CharType*<br/>
Der Typ, der innerhalb eines Programms verwendet wird, um Zeichen zu codieren.

*InputIterator*<br/>
Der Iterator, von dem die Zeitwerte gelesen werden.

## <a name="remarks"></a>Hinweise

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in **id** gespeichert.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|Beschreibung|
|-|-|
|[time_get](#time_get)|Der Konstruktor für Objekte des Typs `time_get`.|

### <a name="typedefs"></a>Typedefs

|Typname|Beschreibung|
|-|-|
|[char_type](#char_type)|Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.|
|[iter_type](#iter_type)|Ein Typ, der einen Eingabeiterator beschreibt.|

### <a name="member-functions"></a>Memberfunktionen

|Member-Funktion|Beschreibung|
|-|-|
|[date_order](#date_order)|Gibt die Datumsreihenfolge zurück, die von einem Facet verwendet wird.|
|[do_date_order](#do_date_order)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um die von einem Facet verwendete Datumsreihenfolge zurückzugeben.|
|[do_get](#do_get)|Liest und konvertiert Zeichendaten in einen Zeitwert.|
|[do_get_date](#do_get_date)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine Zeichenfolge als das Datum zu analysieren, das vom `x`-Bezeichner für `strftime` erstellt wurde.|
|[do_get_monthname](#do_get_monthname)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine Zeichenfolge als Name des Monats zu analysieren.|
|[do_get_time](#do_get_time)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine Zeichenfolge als das Datum zu analysieren, das vom `X`-Bezeichner für `strftime` erstellt wurde.|
|[do_get_weekday](#do_get_weekday)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine Zeichenfolge als Name des Wochentags zu analysieren.|
|[do_get_year](#do_get_year)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine Zeichenfolge als Name des Jahres zu analysieren.|
|[get](#get)|Liest aus einer Zeichendatenquelle und konvertiert die Daten in eine Zeit, die in einer Zeitstruktur gespeichert wird.|
|[get_date](#get_date)|Analysiert eine Zeichenfolge als das Datum, das vom `x`-Bezeichner für `strftime` erzeugt wird.|
|[get_monthname](#get_monthname)|Analysiert eine Zeichenfolge als Name des Monats.|
|[get_time](#get_time)|Analysiert eine Zeichenfolge als das Datum, das vom `X`-Bezeichner für `strftime` erzeugt wird.|
|[get_weekday](#get_weekday)|Analysiert eine Zeichenfolge als Name des Wochentags.|
|[get_year](#get_year)|Analysiert eine Zeichenfolge als Name des Jahres.|

## <a name="requirements"></a>Anforderungen

**Header:** \<locale>

**Namespace:** std

## <a name="char_type"></a> time_get::char_type

Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Synonym für den Vorlagenparameter **CharType**.

## <a name="date_order"></a> time_get::date_order

Gibt die Datumsreihenfolge zurück, die von einem Facet verwendet wird.

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>Rückgabewert

Datumsreihenfolge, die von einem Facet verwendet wird.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt [do_date_order](#do_date_order) zurück.

### <a name="example"></a>Beispiel

```cpp
// time_get_date_order.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
void po( char *p )
{
   locale loc( p );

   time_get <char>::dateorder order = use_facet <time_get <char> >( loc ).date_order ( );
   cout << loc.name( );
   switch (order){
      case time_base::dmy: cout << "(day, month, year)" << endl;
      break;
      case time_base::mdy: cout << "(month, day, year)" << endl;
      break;
      case time_base::ydm: cout << "(year, day, month)" << endl;
      break;
      case time_base::ymd: cout << "(year, month, day)"<< endl;
      break;
      case time_base::no_order: cout << "(no_order)"<< endl;
      break;
   }
}

int main( )
{
   po( "C" );
   po( "german" );
   po( "English_Britain" );
}
```

```Output
C(month, day, year)
German_Germany.1252(day, month, year)
English_United Kingdom.1252(day, month, year)
```

## <a name="do_date_order"></a> time_get::do_date_order

Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um die von einem Facet verwendete Datumsreihenfolge zurückzugeben.

```cpp
virtual dateorder do_date_order() const;
```

### <a name="return-value"></a>Rückgabewert

Datumsreihenfolge, die von einem Facet verwendet wird.

### <a name="remarks"></a>Hinweise

Die virtuelle geschützte Memberfunktion gibt einen Wert vom Typ **time_base::dateorder** zurück, der die Reihenfolge beschreibt, in der Datumskomponenten von [do_get_date](#do_get_date) zugeordnet werden. In dieser Implementierung ist der Wert **time_base::mdy** und entspricht Datumsangaben der Form Dezember 2, 1979.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [date_order](#date_order), mit dem `do_date_order` aufgerufen wird.

## <a name="do_get"></a> time_get::do_get

Liest und konvertiert Zeichendaten in einen Zeitwert. Verwendet einen Konvertierungsspezifizierer und -modifizierer.

```cpp
virtual iter_type
    do_get(
iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Ein Eingabeiterator, der den Anfang der zu konvertierenden Sequenz angibt.

*last*<br/>
Ein Eingabeiterator, der das Ende der Sequenz angibt.

*iosbase*<br/>
Ein Streamobjekt.

*state*<br/>
Ein Feld in Iosbase, in dem entsprechende bitmaskenelemente festgelegt werden, um Fehler anzugeben.

*ptm*<br/>
Ein Zeiger auf die Zeitstruktur, in der die Zeit gespeichert werden soll.

*fmt*<br/>
Eine Konvertierungsspezifiziererzeichen.

*mod*<br/>
Ein optionales Modifiziererzeichen.

### <a name="return-value"></a>Rückgabewert

Gibt einen Iterator zurück, der das erste nicht konvertierte Element kennzeichnet. Ein Konvertierungsfehler bewirkt, dass `ios_base::failbit` in `state` und gibt *erste*.

### <a name="remarks"></a>Hinweise

Die virtuelle Memberfunktion konvertiert und überspringt mindestens ein oder mehrere Elemente im Bereich Eingabe [`first`, `last`) zur Bestimmung der Werte in eine oder mehrere Mitglieder der gespeicherten `*pt`. Ein Konvertierungsfehler bewirkt, dass `ios_base::failbit` in `state` und gibt *erste*. Andernfalls gibt die Funktion einen Iterator zurück, der das erste nicht konvertierte Element festlegt.

Es gibt die folgenden Konvertierungsspezifizierer:

`'a'` oder `'A'` – bewirkt dasselbe Verhalten wie [time_get::get_weekday](#get_weekday).

`'b'`, `'B'` oder `'h'` – bewirkt dasselbe Verhalten wie [time_get::get_monthname](#get_monthname).

`'c'` – bewirkt dasselbe Verhalten wie `"%b %d %H : %M : %S %Y"`.

`'C'` – konvertiert ein dezimales Eingabefeld im Bereich [0, 99] in den Wert `val` und speichert `val * 100 - 1900` in `pt-&tm_year`.

`'d'` oder `'e'` – konvertiert ein dezimales Eingabefeld im Bereich [1, 31] und speichert den Wert in `pt-&tm_mday`.

`'D'` – bewirkt dasselbe Verhalten wie `"%m / %d / %y"`.

`'H'` – konvertiert ein dezimales Eingabefeld im Bereich [0, 23] und speichert dessen Wert in `pt-&tm_hour`.

`'I'` – konvertiert ein dezimales Eingabefeld im Bereich [0, 11] und speichert dessen Wert in `pt-&tm_hour`.

`'j'` – konvertiert ein dezimales Eingabefeld im Bereich [1, 366] und speichert dessen Wert in `pt-&tm_yday`.

`'m'` – konvertiert ein dezimales Eingabefeld im Bereich [1, 12] in den Wert `val` und speichert `val - 1` in `pt-&tm_mon`.

`'M'` – konvertiert ein dezimales Eingabefeld im Bereich [0, 59] und speichert dessen Wert in `pt-&tm_min`.

`'n'` oder `'t'` – bewirkt dasselbe Verhalten wie `" "`.

`'p'` – konvertiert „AM“ oder „am“ in 0 und „PM“ oder „PM“ in 12 und addiert diesen Wert zu `pt-&tm_hour` hinzu.

`'r'` – bewirkt dasselbe Verhalten wie `"%I : %M : %S %p"`.

`'R'` – bewirkt dasselbe Verhalten wie `"%H %M"`.

`'S'` – konvertiert ein dezimales Eingabefeld im Bereich [0, 59] und speichert dessen Wert in `pt-&tm_sec`.

`'T'` oder `'X'` – bewirkt dasselbe Verhalten wie `"%H : %M : S"`.

`'U'` – konvertiert ein dezimales Eingabefeld im Bereich [0, 53] und speichert dessen Wert in `pt-&tm_yday`.

`'w'` – konvertiert ein dezimales Eingabefeld im Bereich [0, 6] und speichert dessen Wert in `pt-&tm_wday`.

`'W'` – konvertiert ein dezimales Eingabefeld im Bereich [0, 53] und speichert dessen Wert in `pt-&tm_yday`.

`'x'` – bewirkt dasselbe Verhalten wie `"%d / %m / %y"`.

`'y'` – konvertiert ein dezimales Eingabefeld im Bereich [0, 99] in den Wert `val` und speichert `val < 69  val + 100 : val` in `pt-&tm_year`.

`'Y'` – bewirkt dasselbe Verhalten wie [time_get::get_year](#get_year).

Jeder andere Konvertierungsspezifizierer bewirkt, dass `ios_base::failbit` in `state` festgelegt wird und ein Rücksprung erfolgt. In dieser Implementierung wirkt sich keiner der Modifizierer aus.

## <a name="do_get_date"></a> time_get::do_get_date

Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine Zeichenfolge als das Datum zu analysieren, das vom *x*-Bezeichner für `strftime` erstellt wurde.

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Der Eingabeiterator, der den Anfang der zu konvertierenden Sequenz adressiert.

*last*<br/>
Der Eingabeiterator, der das Ende der zu konvertierenden Sequenz adressiert.

*iosbase*<br/>
Ein Formatkennzeichen, das bei Verwendung angibt, dass das Währungssymbol optional ist. Ansonsten ist das Währungssymbol erforderlich.

*state*<br/>
Legt die entsprechenden Bitmaskenelemente für den Streamstatus fest, je nachdem, ob die Vorgänge erfolgreich waren.

*ptm*<br/>
Ein Zeiger auf den Ort, an dem die Datumsinformation gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Eingabeiterator,der das erste Element nach dem Eingabefeld adressiert.

### <a name="remarks"></a>Hinweise

Die virtuelle geschützte Memberfunktion versucht, sequenzielle Elemente zuzuordnen, und beginnt zuerst in der Sequenz [ `first`, `last`), bis sie ein vollständiges, nicht leeres Datumseingabefeld erkannt hat. Wenn erfolgreich, sie dieses Feld in seinen äquivalenten Wert als Komponenten konvertiert **tm::tm\_Mon**, **tm::tm\_Tag**, und **tm::tm\_Jahr** , und speichert die Ergebnisse in `ptm->tm_mon`, `ptm->tm_day`, und `ptm->tm_year`bzw. Sie gibt einen Iterator zurück, der das erste Element nach dem Datumseingabefeld festlegt. Andernfalls legt die Funktion fest `iosbase::failbit` in *Zustand*. Sie gibt einen Iterator zurück, der das erste Element nach jedem Präfix eines gültigen Datumseingabefelds festlegt. In beiden Fällen, wenn der Rückgabewert *letzten*, legt die Funktion `ios_base::eofbit` in *Zustand*.

Das Format für das Datumseingabefeld ist vom Gebietsschema abhängig. Für das Standardgebietsschema hat das Datumseingabefeld die Form MMM DD, YYYY:

- MMM wird durch Aufrufen von [get_monthname](#get_monthname) abgeglichen, das den Monat angibt.

- DD ist eine Folge von Dezimalziffern, deren entsprechender numerischer Wert im Bereich [1, 31] liegen muss und den Tag des Monats angibt.

- YYYY wird durch Aufrufen von [get_year](#get_year) abgeglichen, das das Jahr angibt.

Die literalen Leerzeichen und Kommas müssen mit den entsprechenden Elementen in der Eingabesequenz übereinstimmen.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [get_date](#get_date), mit dem `do_get_date` aufgerufen wird.

## <a name="do_get_monthname"></a> time_get::do_get_monthname

Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine Zeichenfolge als Name des Monats zu analysieren.

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Der Eingabeiterator, der den Anfang der zu konvertierenden Sequenz adressiert.

*last*<br/>
Der Eingabeiterator, der das Ende der zu konvertierenden Sequenz adressiert.

*iosbase*<br/>
Nicht verwendet.

*state*<br/>
Ein Ausgabeparameter, der die entsprechenden Bitmaskenelemente für den Streamstatus festlegt, je nachdem, ob die Vorgänge erfolgreich waren.

*ptm*<br/>
Ein Zeiger auf den Ort, an dem die Monatsinformation gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Eingabeiterator,der das erste Element nach dem Eingabefeld adressiert.

### <a name="remarks"></a>Hinweise

Die virtuelle geschützte Memberfunktion versucht, sequenzielle Elemente zuzuordnen, und beginnt zuerst in der Sequenz [ `first`, `last`), bis sie ein vollständiges, nicht leeres Monatseingabefeld erkannt hat. Wenn erfolgreich, sie dieses Feld in seinen äquivalenten Wert als Komponente konvertiert **tm::tm\_Mon**, und speichert das Ergebnis in `ptm->tm_mon`. Sie gibt einen Iterator zurück, der das erste Element nach dem Monatseingabefeld festlegt. Andernfalls legt die Funktion fest `ios_base::failbit` in *Zustand*. Sie gibt einen Iterator zurück, der das erste Element nach jedem Präfix eines gültigen Monatseingabefelds festlegt. In beiden Fällen, wenn der Rückgabewert *letzten*, legt die Funktion `ios_base::eofbit` in *Zustand*.

Das Monatseingabefeld ist eine Sequenz, die die längste aus einer Reihe von gebietsschemaspezifischen Zeichenfolgen wie Jan, Januar, Feb, Februar usw. zuordnet. Der konvertierte Wert ist die Anzahl von Monaten seit Januar.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [get_monthname](#get_monthname), mit dem `do_get_monthname` aufgerufen wird.

## <a name="do_get_time"></a> time_get::do_get_time

Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine Zeichenfolge als das Datum zu analysieren, das vom *X*-Bezeichner für `strftime` erstellt wurde.

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Der Eingabeiterator, der den Anfang der zu konvertierenden Sequenz adressiert.

*last*<br/>
Der Eingabeiterator, der das Ende der zu konvertierenden Sequenz adressiert.

*iosbase*<br/>
Nicht verwendet.

*state*<br/>
Legt die entsprechenden Bitmaskenelemente für den Streamstatus fest, je nachdem, ob die Vorgänge erfolgreich waren.

*ptm*<br/>
Ein Zeiger auf den Ort, an dem die Datumsinformation gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Eingabeiterator,der das erste Element nach dem Eingabefeld adressiert.

### <a name="remarks"></a>Hinweise

Die virtuelle geschützte Memberfunktion versucht, sequenzielle Elemente zuzuordnen, und beginnt zuerst in der Sequenz [ `first`, `last`), bis sie ein vollständiges, nicht leeres Zeiteingabefeld erkannt hat. Wenn erfolgreich, sie dieses Feld in seinen äquivalenten Wert als Komponenten konvertiert `tm::tm_hour`, `tm::tm_min`, und `tm::tm_sec`, und speichert die Ergebnisse in `ptm->tm_hour`, `ptm->tm_min`, und `ptm->tm_sec`bzw. Sie gibt einen Iterator zurück, der das erste Element nach dem Zeiteingabefeld festlegt. Andernfalls legt die Funktion fest `ios_base::failbit` in *Zustand*. Sie gibt einen Iterator zurück, der das erste Element nach jedem Präfix eines gültigen Zeiteingabefelds festlegt. In beiden Fällen, wenn der Rückgabewert *letzten*, legt die Funktion `ios_base::eofbit` in *Zustand*.

In dieser Implementierung hat das Zeiteingabefeld die Form HH:MM:SS:

- HH ist eine Folge von Dezimalziffern, deren entsprechender numerischer Wert im Bereich [0, 24) liegen muss und die Stunde des Tages angibt.

- MM ist eine Folge von Dezimalziffern, deren entsprechender numerischer Wert im Bereich [0, 60) liegen muss und die Minuten nach der Stunde angibt.

- SS ist eine Folge von Dezimalziffern, deren entsprechender numerischer Wert im Bereich [0, 60) liegen muss und die Sekunden nach der Minute angibt.

Die literalen Doppelpunkte müssen mit den entsprechenden Elementen in der Eingabesequenz übereinstimmen.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [get_time](#get_time), mit dem `do_get_time` aufgerufen wird.

## <a name="do_get_weekday"></a> time_get::do_get_weekday

Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine Zeichenfolge als Name des Wochentags zu analysieren.

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Der Eingabeiterator, der den Anfang der zu konvertierenden Sequenz adressiert.

*last*<br/>
Der Eingabeiterator, der das Ende der zu konvertierenden Sequenz adressiert.

*iosbase*<br/>
Ein Formatkennzeichen, das bei Verwendung angibt, dass das Währungssymbol optional ist. Ansonsten ist das Währungssymbol erforderlich.

*state*<br/>
Legt die entsprechenden Bitmaskenelemente für den Streamstatus fest, je nachdem, ob die Vorgänge erfolgreich waren.

*ptm*<br/>
Ein Zeiger auf den Ort, an dem die Wochentagsinformation gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Eingabeiterator,der das erste Element nach dem Eingabefeld adressiert.

### <a name="remarks"></a>Hinweise

Die virtuelle geschützte Memberfunktion versucht, sequenzielle Elemente ab *erste* in der Sequenz [ `first`, `last`) bis ein vollständiges erkannt hat, nicht leeres wochentagseingabefeld. Wenn erfolgreich, sie dieses Feld in seinen äquivalenten Wert als Komponente konvertiert **tm::tm\_"wDay"**, und speichert das Ergebnis in `ptm->tm_wday`. Sie gibt einen Iterator zurück, der das erste Element nach dem Wochentagseingabefeld festlegt. Andernfalls legt die Funktion fest `ios_base::failbit` in *Zustand*. Sie gibt einen Iterator zurück, der das erste Element nach jedem Präfix eines gültigen Wochentagseingabefelds festlegt. In beiden Fällen, wenn der Rückgabewert *letzten*, legt die Funktion `ios_base::eofbit` in *Zustand*.

Das Wochentagseingabefeld ist eine Sequenz, die die längste aus einer Reihe von gebietsschemaspezifischen Zeichenfolgen wie So, Sonntag, Mo, Montag usw. zuordnet. Der konvertierte Wert ist die Anzahl von Tagen seit Sonntag.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [get_weekday](#get_weekday), mit dem `do_get_weekday` aufgerufen wird.

## <a name="do_get_year"></a> time_get::do_get_year

Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine Zeichenfolge als Name des Jahres zu analysieren.

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Der Eingabeiterator, der den Anfang der zu konvertierenden Sequenz adressiert.

*last*<br/>
Der Eingabeiterator, der das Ende der zu konvertierenden Sequenz adressiert.

*iosbase*<br/>
Ein Formatkennzeichen, das bei Verwendung angibt, dass das Währungssymbol optional ist. Ansonsten ist das Währungssymbol erforderlich.

*state*<br/>
Legt die entsprechenden Bitmaskenelemente für den Streamstatus fest, je nachdem, ob die Vorgänge erfolgreich waren.

*ptm*<br/>
Ein Zeiger auf den Ort, an dem die Jahresinformation gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Eingabeiterator,der das erste Element nach dem Eingabefeld adressiert.

### <a name="remarks"></a>Hinweise

Die virtuelle geschützte Memberfunktion versucht, sequenzielle Elemente ab *erste* in der Sequenz [ `first`, `last`) bis ein vollständiges erkannt hat, nicht leeres jahreseingabefeld. Wenn erfolgreich, sie dieses Feld in seinen äquivalenten Wert als Komponente konvertiert **tm::tm\_Jahr**, und speichert das Ergebnis in `ptm->tm_year`. Sie gibt einen Iterator zurück, der das erste Element nach dem Jahreseingabefeld festlegt. Andernfalls legt die Funktion fest `ios_base::failbit` in *Zustand*. Sie gibt einen Iterator zurück, der das erste Element nach jedem Präfix eines gültigen Jahreseingabefelds festlegt. In beiden Fällen, wenn der Rückgabewert *letzten*, legt die Funktion `ios_base::eofbit` in *Zustand*.

Das Jahreseingabefeld ist eine Folge von Dezimalziffern, deren entsprechender numerischer Wert im Bereich [1900, 2036) liegen muss. Der gespeicherte Wert ist dieser Wert minus 1900. In dieser Implementierung repräsentieren Werte im Bereich [69, 136) den Bereich von Jahren [1969, 2036). Werte im Bereich [0, 69) sind ebenfalls zulässig, können jedoch abhängig von der jeweiligen Übersetzungsumgebung entweder den Bereich von Jahren [1900, 1969) oder [2000, 2069) darstellen.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [get_year](#get_year), mit dem `do_get_year` aufgerufen wird.

## <a name="get"></a> time_get::get

Liest aus einer Zeichendatenquelle und konvertiert die Daten in eine Zeit, die in einer Zeitstruktur gespeichert wird. Die erste Funktion akzeptiert einen Konvertierungsspezifizierer und -modifizierer, die zweite akzeptiert mehrere.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char_type* fmt_first,
    char_type* fmt_last) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Eingabeiterator, der angibt, wo die zu konvertierende Sequenz beginnt.

*last*<br/>
Eingabeiterator, der das Ende der zu konvertierenden Sequenz angibt.

*iosbase*<br/>
Der Stream (Datenstrom).

*state*<br/>
Die entsprechenden Bitmaskenelemente werden für den Streamzustand festgelegt, um Fehler zu kennzeichnen.

*ptm*<br/>
Zeiger auf die Zeitstruktur, in der die Zeit gespeichert werden soll.

*fmt*<br/>
Eine Konvertierungsspezifiziererzeichen.

*mod*<br/>
Ein optionales Modifiziererzeichen.

*fmt_first*<br/>
Zeigt auf die Stelle, an der die Formatanweisungen beginnen.

*fmt_last*<br/>
Zeigt auf das Ende der Formatanweisungen.

### <a name="return-value"></a>Rückgabewert

Gibt einen Iterator zum ersten Zeichen zurück, nachdem die Daten, die zum Zuordnen der Uhrzeit-Struktur verwendet wurde `*ptm`.

### <a name="remarks"></a>Hinweise

Die erste Memberfunktion gibt `do_get(first, last, iosbase, state, ptm, fmt, mod)` zurück.

Die zweite Memberfunktion ruft `do_get` unter der Kontrolle des Formats auf, das durch `[fmt_first, fmt_last)` begrenzt ist. Die Funktion behandelt das Format als Sequenz von Feldern, von denen jedes die Konvertierung von null oder mehr Eingabeelementen bestimmt, die durch `[first, last)` begrenzt sind. Sie gibt einen Iterator zurück, der das erste nicht konvertierte Element festlegt. Es gibt drei Arten von Feldern:

Ein Prozentzeichen (%) in das Format, gefolgt von der ein optionaler Modifizierer *mod* im festgelegten [eoq#], gefolgt von einem Konvertierungsspezifizierer *Fmt*, ersetzt *erste* mit den Rückgabewert von `do_get(first, last, iosbase, state, ptm, fmt, mod)`. Ein Konvertierungsfehler bewirkt, dass `ios_base::failbit` in *Zustand* und zurückgibt.

Ein Leerzeichenelement im Format bewirkt ein Überspringen von eingegebenen Leerzeichenelementen.

Jedes weitere Element im Format muss mit dem nächsten Eingabeelement übereinstimmen, das übersprungen wird. Ein Übereinstimmungsfehler bewirkt, dass `ios_base::failbit` in *Zustand* und zurückgibt.

## <a name="get_date"></a> time_get::get_date

Analysiert eine Zeichenfolge als das Datum, das vom *x*-Bezeichner für `strftime` erzeugt wird.

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Der Eingabeiterator, der den Anfang der zu konvertierenden Sequenz adressiert.

*last*<br/>
Der Eingabeiterator, der das Ende der zu konvertierenden Sequenz adressiert.

*iosbase*<br/>
Ein Formatkennzeichen, das bei Verwendung angibt, dass das Währungssymbol optional ist. Ansonsten ist das Währungssymbol erforderlich.

*state*<br/>
Legt die entsprechenden Bitmaskenelemente für den Streamstatus fest, je nachdem, ob die Vorgänge erfolgreich waren.

*ptm*<br/>
Ein Zeiger auf den Ort, an dem die Datumsinformation gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Eingabeiterator,der das erste Element nach dem Eingabefeld adressiert.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt [Do_get_date](#do_get_date)(`first`, `last`, `iosbase`, `state`, `ptm`).

Beachten Sie, dass Monate von 0 bis 11 gezählt werden.

### <a name="example"></a>Beispiel

```cpp
// time_get_get_date.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset(&t, 0, sizeof(struct tm));

   pszGetF << "July 4, 2000";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get<char> >
   (loc).get_date(basic_istream<char>::_Iter(pszGetF.rdbuf( ) ),
            basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if ( st & ios_base::failbit )
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(July 4, 2000) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 4
tm_mon: 6
tm_year: 100
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="get_monthname"></a> time_get::get_monthname

Analysiert eine Zeichenfolge als Name des Monats.

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Der Eingabeiterator, der den Anfang der zu konvertierenden Sequenz adressiert.

*last*<br/>
Der Eingabeiterator, der das Ende der zu konvertierenden Sequenz adressiert.

*iosbase*<br/>
Nicht verwendet.

*state*<br/>
Ein Ausgabeparameter, der die entsprechenden Bitmaskenelemente für den Streamstatus festlegt, je nachdem, ob die Vorgänge erfolgreich waren.

*ptm*<br/>
Ein Zeiger auf den Ort, an dem die Monatsinformation gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Eingabeiterator,der das erste Element nach dem Eingabefeld adressiert.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt [Do_get_monthname](#do_get_monthname)(`first`, `last`, `iosbase`, `state`, `ptm`).

### <a name="example"></a>Beispiel

```cpp
// time_get_get_monthname.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "juillet";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get <char> >
   (loc).get_monthname(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
              basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(juillet) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 0
tm_mon: 6
tm_year: 0
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="get_time"></a> time_get::get_time

Analysiert eine Zeichenfolge als das Datum, das vom *X*-Bezeichner für `strftime` erzeugt wird.

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Der Eingabeiterator, der den Anfang der zu konvertierenden Sequenz adressiert.

*last*<br/>
Der Eingabeiterator, der das Ende der zu konvertierenden Sequenz adressiert.

*iosbase*<br/>
Nicht verwendet.

*state*<br/>
Legt die entsprechenden Bitmaskenelemente für den Streamstatus fest, je nachdem, ob die Vorgänge erfolgreich waren.

*ptm*<br/>
Ein Zeiger auf den Ort, an dem die Datumsinformation gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Eingabeiterator,der das erste Element nach dem Eingabefeld adressiert.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt [Do_get_time](#do_get_time)(`first`, `last`, `iosbase`, `state`, `ptm`).

### <a name="example"></a>Beispiel

```cpp
// time_get_get_time.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "11:13:20";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get <char> >
      (loc).get_time(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << endl;
}
```

```Output
time_get::get_time(11:13:20) =
tm_sec: 20
tm_min: 13
tm_hour: 11
```

## <a name="get_weekday"></a> time_get::get_weekday

Analysiert eine Zeichenfolge als Name des Wochentags.

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Der Eingabeiterator, der den Anfang der zu konvertierenden Sequenz adressiert.

*last*<br/>
Der Eingabeiterator, der das Ende der zu konvertierenden Sequenz adressiert.

*iosbase*<br/>
Ein Formatkennzeichen, das bei Verwendung angibt, dass das Währungssymbol optional ist. Ansonsten ist das Währungssymbol erforderlich.

*state*<br/>
Legt die entsprechenden Bitmaskenelemente für den Streamstatus fest, je nachdem, ob die Vorgänge erfolgreich waren.

*ptm*<br/>
Ein Zeiger auf den Ort, an dem die Wochentagsinformation gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Eingabeiterator,der das erste Element nach dem Eingabefeld adressiert.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt [Do_get_weekday](#do_get_weekday)(`first`, `last`, `iosbase`, `state`, `ptm`).

### <a name="example"></a>Beispiel

```cpp
// time_get_get_weekday.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "mercredi";
   pszGetF.imbue(loc);
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_weekday(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_wday: " << t.tm_wday
      << endl;
}
```

```Output
time_get::get_time(mercredi) =
tm_wday: 3
```

## <a name="get_year"></a> time_get::get_year

Analysiert eine Zeichenfolge als Name des Jahres.

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parameter

*first*<br/>
Der Eingabeiterator, der den Anfang der zu konvertierenden Sequenz adressiert.

*last*<br/>
Der Eingabeiterator, der das Ende der zu konvertierenden Sequenz adressiert.

*iosbase*<br/>
Ein Formatkennzeichen, das bei Verwendung angibt, dass das Währungssymbol optional ist. Ansonsten ist das Währungssymbol erforderlich.

*state*<br/>
Legt die entsprechenden Bitmaskenelemente für den Streamstatus fest, je nachdem, ob die Vorgänge erfolgreich waren.

*ptm*<br/>
Ein Zeiger auf den Ort, an dem die Jahresinformation gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Eingabeiterator,der das erste Element nach dem Eingabefeld adressiert.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt [Do_get_year](#do_get_year)(`first`, `last`, `iosbase`, `state`, `ptm`).

### <a name="example"></a>Beispiel

```cpp
// time_get_get_year.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "1928";

   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_year(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_year: " << t.tm_year
      << endl;
}
```

```Output
time_get::get_year(1928) =
tm_year: 28
```

## <a name="iter_type"></a> time_get::iter_type

Ein Typ, der einen Eingabeiterator beschreibt.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Hinweise

Der Type ist ein Synonym für den Vorlagenparameter **InputIterator**.

## <a name="time_get"></a> time_get::time_get

Der Konstruktor für Objekte des Typs `time_get`.

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>Parameter

*refs*<br/>
Integerwert, der zum Angeben des Speicherverwaltungstyps für das Objekt verwendet wird.

### <a name="remarks"></a>Hinweise

Die möglichen Werte für die *Refs* Parameter und ihre Bedeutung:

- 0: Die Lebensdauer des Objekts wird von den Gebietsschemas verwaltet, die es enthalten ist.

- 1: Die Lebensdauer des Objekts muss manuell verwaltet werden.

- \> 1: Diese Werte sind nicht definiert.

Direkte Beispiele hierfür sind nicht möglich, da der Destruktor geschützt ist.

Der Konstruktor initialisiert sein Basisobjekt mit **Locale::**[Facet](../standard-library/locale-class.md#facet_class)(`refs`).

## <a name="see-also"></a>Siehe auch

[\<locale>](../standard-library/locale.md)<br/>
[time_base-Klasse](../standard-library/time-base-class.md)<br/>
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
