---
title: strtoll, _strtoll_l, wcstoll, _wcstoll_l
ms.date: 11/04/2016
apiname:
- strtoll
- wcstoll
- _strtoll_l
- _wcstoll_l
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strtoll_l
- _tcstoll_l
- _tcstoll
- _wcstoll_l
- strtoll
- wcstoll
helpviewer_keywords:
- _tcstoll_l function
- _wcstoll_l function
- strtoll function
- wcstoll function
- _tcstoll function
- _strtoll_l function
ms.assetid: e2d05dcf-d3b2-4291-9e60-dee77e540fd7
ms.openlocfilehash: 53ae4ab1d482478c50aa257acdc974569bfc05f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269149"
---
# <a name="strtoll-strtolll-wcstoll-wcstolll"></a>strtoll, _strtoll_l, wcstoll, _wcstoll_l

Konvertiert eine Zeichenfolge in eine **lange** **lange** Wert.

## <a name="syntax"></a>Syntax

```C
long long strtoll(
   const char *strSource,
   char **endptr,
   int base
);
long long wcstoll(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
long long _strtoll_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
long long _wcstoll_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*strSource*<br/>
Zu konvertierende mit NULL endende Zeichenfolge.

*endptr*<br/>
Zeiger auf das Zeichen, das die Überprüfung stoppt.

*base*<br/>
Zu verwendende Zahlenbasis.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**Strtoll** gibt den Wert, der dargestellt wird, in der Zeichenfolge *StrSource*, außer wenn die Darstellung würde einen Überlauf verursachen — in diesem Fall gibt **LLONG_MAX** oder **LLONG_MIN**. Die Funktion gibt 0 zurück, wenn keine Konvertierung ausgeführt werden kann. **Wcstoll** gibt Werte analog zu **Strtoll**.

**LLONG_MAX** und **LLONG_MIN** in Grenzen definiert sind. H.

Wenn *StrSource* ist **NULL** oder *Basis* ungleich NULL ist und entweder weniger als 2 oder größer als 36, **Errno** nastaven NA hodnotu **EINVAL** .

Weitere Informationen zu diesen Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **Strtoll** -Funktion konvertiert *StrSource* zu einem **lange** **lange**. Beide Funktionen beenden das Lesen der Zeichenfolge *StrSource* mit dem ersten Zeichen, die sie nicht als Teil einer Zahl erkannt. Dies ist möglicherweise das abschließende Nullzeichen, oder es ist das erste numerische Zeichen, die größer als oder gleich ist *Basis*. **Wcstoll** ist eine Breitzeichen-Version von **Strtoll**, dessen *StrSource* Argument ist eine Breitzeichen-Zeichenfolge. Ansonsten verhalten sich diese Funktionen identisch.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoll**|**strtoll**|**strtoll**|**wcstoll**|
|**_tcstoll_l**|**_strtoll_l**|**_strtoll_l**|**_wcstoll_l**|

Des Gebietsschemas des **LC_NUMERIC** bestimmt das Erkennen des Basiszeichens in *StrSource*; Weitere Informationen finden Sie unter [Setlocale, _wsetlocale](setlocale-wsetlocale.md). Die Funktionen ohne das **_l** -Suffix verwenden das aktuelle Gebietsschema. **_strtoll_l** und **_wcstoll_l** sind identisch mit den entsprechenden Funktionen, die das Suffix haben, verwenden jedoch stattdessen das Gebietsschema, das übergeben wird. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn *Endptr* nicht **NULL**, ein Zeiger auf das Zeichen, die Überprüfung beendet, wird gespeichert, an dem Speicherort, auf das von *Endptr*. Wenn keine Konvertierung ausgeführt werden kann (keine gültigen Ziffern gefunden oder ungültige Basis angegeben) den Wert der *StrSource* wird an dem Speicherort gespeichert, auf das von *Endptr*.

**Strtoll** erwartet *StrSource* auf eine Zeichenfolge der folgenden Form zeigt:

> [*Leerzeichen*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*Ziffern* &#124; *Buchstaben*]  

Ein *Leerzeichen* besteht möglicherweise aus Leerzeichen und Tabulatorzeichen, die ignoriert werden; *Ziffern* sind eine oder mehrere Dezimalstellen sind; *Buchstaben* können eine oder mehrere der Buchstaben "a" bis "Z" (oder "A" bis "Z"). Das erste Zeichen, das dieser Form nicht entspricht, beendet die Überprüfung. Wenn *Basis* zwischen 2 und 36 liegt, ist er als der Basis der Zahl verwendet wird. Wenn *Basis* ist 0, die ersten Zeichen der Zeichenfolge, auf das von *StrSource* werden verwendet, um die Basis festzulegen. Wenn das erste Zeichen "0 " und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als oktale ganze Zahl interpretiert. Wenn das erste Zeichen "0" und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als hexadezimale ganze Zahl interpretiert. Wenn das erste Zeichen "1" bis "9 " ist, wird die Zeichenfolge als ganze Dezimalzahl interpretiert. Den Buchstaben „a“ bis „z“ (bzw. „A“ bis „Z“) werden die Werten 10 bis 35 zugewiesen. Es sind nur Buchstaben zulässig, deren zugewiesene Werte kleiner als *base* sind. Das erste Zeichen außerhalb des Bereichs der Basis beendet die Überprüfung. Z. B. wenn *Basis* ist 0 und das erste überprüfte Zeichen "0", eine ganze Oktalzahl angenommen und ein "8" oder "9"-Zeichen beendet die Überprüfung.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**strtoll**, **_strtoll_l**|\<stdlib.h>|
|**wcstoll**, **_wcstoll_l**|\<stdlib.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funktionen zur Konvertierung von Zeichenfolgen in numerische Werte](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
