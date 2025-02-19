---
title: strtoul, _strtoul_l, wcstoul, _wcstoul_l
ms.date: 11/04/2016
apiname:
- _wcstoul_l
- _strtoul_l
- strtoul
- wcstoul
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- strtoul
- _tcstoul
- wcstoul
helpviewer_keywords:
- _wcstoul_l function
- _tcstoul function
- _strtoul_l function
- string conversion, to integers
- wcstoul function
- strtoul function
- wcstoul_l function
- strtoul_l function
- tcstoul function
ms.assetid: 38f2afe8-8178-4e0b-8bbe-d5c6ad66e3ab
ms.openlocfilehash: d4d974084c9249740d565f879f471bc7dfc697bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269203"
---
# <a name="strtoul-strtoull-wcstoul-wcstoull"></a>strtoul, _strtoul_l, wcstoul, _wcstoul_l

Konvertiert eine Zeichenfolge in einen langen ganzzahligen Wert ohne Vorzeichen.

## <a name="syntax"></a>Syntax

```C
unsigned long strtoul(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long _strtoul_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long wcstoul(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long _wcstoul_l(
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
Zeiger auf ein Zeichen, mit dem die Überprüfung beendet wird.

*base*<br/>
Zu verwendende Zahlenbasis.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**Strtoul** gibt den konvertierten Wert zurück, sofern vorhanden, oder **ULONG_MAX** bei einem Überlauf. **Strtoul** gibt 0 zurück, wenn keine Konvertierung ausgeführt werden kann. **Wcstoul** gibt Werte analog zu **Strtoul**. Für beide Funktionen **Errno** nastaven NA hodnotu **ERANGE** Wenn Überlauf oder Unterlauf auftritt.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Hinweise

Jede dieser Funktionen konvertiert die Eingabezeichenfolge *StrSource* auf eine **ohne Vorzeichen** **lange**.

**Strtoul** stoppt das Lesen der Zeichenfolge *StrSource* mit dem ersten Zeichen, die nicht als Teil einer Zahl erkannt. Dies ist möglicherweise das abschließende Nullzeichen, oder es ist das erste numerische Zeichen größer als oder gleich *Basis*. Die **LC_NUMERIC** -kategorieeinstellung des Gebietsschemas bestimmt das Erkennen des Basiszeichens in *StrSource*; Weitere Informationen finden Sie unter [Setlocale](setlocale-wsetlocale.md). **Strtoul** und **Wcstoul** verwenden das aktuelle Gebietsschema. **_strtoul_l** und **_wcstoul_l** sind identisch, allerdings das übergebene Gebietsschema verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn *Endptr* nicht **NULL**, ein Zeiger auf das Zeichen, die Überprüfung beendet, wird gespeichert, an der Position zeigt *Endptr*. Wenn keine Konvertierung ausgeführt werden kann (keine gültigen Ziffern gefunden oder ungültige Basis angegeben) den Wert der *StrSource* befindet sich in den Speicherort verweist *Endptr*.

**Wcstoul** ist eine Breitzeichen-Version von **Strtoul**, dessen *StrSource* Argument ist eine Breitzeichen-Zeichenfolge. Anderenfalls verhalten sich diese Funktionen identisch.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoul**|**strtoul**|**strtoul**|**wcstoul**|
|**_tcstoul_l**|**strtoul_l**|**_strtoul_l**|**_wcstoul_l**|

**Strtoul** erwartet *StrSource* auf eine Zeichenfolge der folgenden Form zeigt:

> [*Leerzeichen*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*Ziffern* &#124; *Buchstaben*]  

Ein *Leerzeichen* besteht möglicherweise aus Leerzeichen und Tabulatorzeichen, die ignoriert werden. *Ziffern* sind eine oder mehrere Dezimalstellen. *Buchstaben* können eine oder mehrere der Buchstaben "a" bis "Z" (oder "A" bis "Z"). Das erste Zeichen, das dieser Form nicht entspricht, beendet die Überprüfung. Wenn *Basis* zwischen 2 und 36 liegt, ist er als der Basis der Zahl verwendet wird. Wenn *Basis* ist 0, die ersten Zeichen der Zeichenfolge verweist *StrSource* werden verwendet, um die Basis festzulegen. Wenn das erste Zeichen "0" und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als ganze Oktalzahl interpretiert. Wenn das erste Zeichen "0" und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als hexadezimale ganze Zahl interpretiert. Wenn das erste Zeichen "1" bis "9 " ist, wird die Zeichenfolge als ganze Dezimalzahl interpretiert. Den Buchstaben „a“ bis „z“ (bzw. „A“ bis „Z“) werden die Werten 10 bis 35 zugewiesen. Es sind nur Buchstaben zulässig, deren zugewiesene Werte kleiner als *base* sind. Das erste Zeichen außerhalb des Bereichs der Basis beendet die Überprüfung. Z. B. wenn *Basis* ist 0 und das erste überprüfte Zeichen "0", eine ganze Oktalzahl angenommen und ein "8" oder "9"-Zeichen beendet die Überprüfung. **Strtoul** lässt ein Pluszeichen (**+**) oder ein Minuszeichens (**-**) zeichenpräfix; ein führendes Minuszeichen gibt an, dass der Rückgabewert invertiert wird.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**strtoul**|\<stdlib.h>|
|**wcstoul**|\<stdlib.h> oder \<wchar.h>|
|**_strtoul_l**|\<stdlib.h>|
|**_wcstoul_l**|\<stdlib.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funktionen zur Konvertierung von Zeichenfolgen in numerische Werte](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
