---
title: strtof, _strtof_l, wcstof, _wcstof_l
ms.date: 04/05/2018
apiname:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
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
- _tcstof
- _tcstof_l
- stdlib/strtof
- strtof
- stdlib/_strtof_l
- _strtof_l
- corecrt_wstdlib/wcstof
- wcstof
- corecrt_wstdlib/_wcstof_l
- _wcstof_l
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
ms.openlocfilehash: 10a50a175685f3e8f7f1241683c7705fd9a9b142
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376431"
---
# <a name="strtof-strtofl-wcstof-wcstofl"></a>strtof, _strtof_l, wcstof, _wcstof_l

Konvertiert eine Zeichenfolge in einen Gleitkommawert mit einfacher Genauigkeit.

## <a name="syntax"></a>Syntax

```C
float strtof(
   const char *strSource,
   char **endptr
);
float _strtof_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
float wcstof(
   const wchar_t *strSource,
   wchar_t **endptr
);
float wcstof_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

## <a name="parameters"></a>Parameter

*strSource*<br/>
Zu konvertierende mit NULL endende Zeichenfolge.

*endptr*<br/>
Zeiger auf das Zeichen, das die Überprüfung stoppt.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**Strtof** gibt den Wert der Gleitkommazahl, außer wenn die Darstellung würde einen Überlauf, verursachen in dem Fall wird die Funktion zurückgegeben werden, +/-**HUGE_VALF**. Das Vorzeichen des **HUGE_VALF** entspricht dem Zeichen des Werts, der nicht dargestellt werden kann. **Strtof** gibt 0 zurück, wenn keine Konvertierung ausgeführt werden kann oder ein Unterlauf auftritt.

**Wcstof** gibt Werte analog zu **Strtof**. Für beide Funktionen **Errno** nastaven NA hodnotu **ERANGE** Überlauf oder Unterlauf auftritt und der Handler für ungültige Parameter aufgerufen, siehe [Parametervalidierung](../../c-runtime-library/parameter-validation.md).

Weitere Informationen zu diesen Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Jede Funktion wandelt die Eingabezeichenfolge *StrSource* zu einem **"float"**. Die **Strtof** -Funktion konvertiert *StrSource* auf einen Wert mit einfacher Genauigkeit. **Strtof** stoppt das Lesen der Zeichenfolge *StrSource* mit dem ersten Zeichen, die nicht als Teil einer Zahl erkannt. Dies ist möglicherweise das beendende NULL-Zeichen. **Wcstof** ist eine Breitzeichen-Version von **Strtof**, dessen *StrSource* Argument ist eine Breitzeichen-Zeichenfolge. Ansonsten verhalten sich diese Funktionen identisch.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

Die **LC_NUMERIC** -kategorieeinstellung des aktuellen Gebietsschemas bestimmt das Erkennen des Basiszeichens in *StrSource*; Weitere Informationen finden Sie unter [Setlocale, _wsetlocale](setlocale-wsetlocale.md). Die Funktionen ohne das **_l** Suffix verwenden das aktuelle Gebietsschema; diejenigen, die das Suffix sind identisch, außer dass sie das Gebietsschema verwenden, die stattdessen übergeben wird. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn *Endptr* nicht **NULL**, ein Zeiger auf das Zeichen, die Überprüfung beendet, wird gespeichert, an dem Speicherort, auf das von *Endptr*. Wenn keine Konvertierung ausgeführt werden kann (keine gültigen Ziffern gefunden oder ungültige Basis angegeben) den Wert der *StrSource* wird an dem Speicherort gespeichert, auf das von *Endptr*.

**Strtof** erwartet *StrSource* auf eine Zeichenfolge der folgenden Form zeigt:

[*Leerzeichen*] [*anmelden*] [*Ziffern*] [__.__ *Ziffern*] [{**e** &#124; **E**} [*anmelden*] *Ziffern*]

Ein *Leerzeichen* besteht möglicherweise aus Leerzeichen und Tabulatorzeichen, die ignoriert werden; *anmelden* ist entweder plus (**+**) oder ein Minuszeichens (**-**); und *Ziffern* sind eine oder mehrere Dezimalstellen. Wenn keine Ziffern vor dem Basiszeichen stehen, muss mindestens eine Ziffer nach dem Basiszeichen stehen. Die Dezimalstellen können ein Exponent, der besteht aus einem einführenden Buchstaben folgen (**e** oder **E**) und einer optional Zahl mit Vorzeichen. Wenn weder ein Exponententeil noch ein Basiszeichen angezeigt wird, wird davon ausgegangen, dass ein Basiszeichen auf die letzte Ziffer in der Zeichenfolge folgt. Das erste Zeichen, das dieser Form nicht entspricht, beendet die Überprüfung.

Die UCRT-Versionen dieser Funktionen unterstützen keine Konvertierung von Fortran-Stil (**d** oder **D**) Buchstaben in Exponenten. Diese nicht-standardmäßige Erweiterung wurde in früheren Versionen der CRT unterstützt. Sie ist möglicherweise eine fehlerhafte Änderung für Ihren Code.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**strtof**, **_strtof_l**|C: \<stdlib.h> C++: &lt;cstdlib> oder \<stdlib.h>|
|**wcstof**, **_wcstof_l**|C: \<stdlib.h> oder \<wchar.h> C++: &lt;cstdlib>, \<stdlib.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_strtof.c
// This program uses strtof to convert a
// string to a single-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   float x;

   string = "3.14159This stopped it";
   x = strtof(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtof = %f\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.14159This stopped it
   strtof = 3.141590
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Funktionen zur Konvertierung von Zeichenfolgen in numerische Werte](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
