---
title: _fcvt_s
ms.date: 04/05/2018
apiname:
- _fcvt_s
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
- fcvt_s
- _fcvt_s
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
ms.openlocfilehash: 51ff3c675f1f53aee9beab629b17193164a2e7eb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334865"
---
# <a name="fcvts"></a>_fcvt_s

Konvertiert eine Gleitkommazahl in eine Zeichenfolge. Dies ist eine sicherere Version von [_fcvt](fcvt.md), wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t _fcvt_s(
   char* buffer,
   size_t sizeInBytes,
   double value,
   int count,
   int *dec,
   int *sign
);
template <size_t size>
errno_t _fcvt_s(
   char (&buffer)[size],
   double value,
   int count,
   int *dec,
   int *sign
); // C++ only
```

### <a name="parameters"></a>Parameter

*buffer*<br/>
Der angegebene Puffer, der das Ergebnis der Konvertierung enthält.

*sizeInBytes*<br/>
Die Größe des Puffers in Byte.

*value*<br/>
Zu konvertierende Zahl.

*count*<br/>
Anzahl der Ziffern nach dem Dezimaltrennzeichen.

*dec*<br/>
Zeiger auf die gespeicherte Position der Dezimalstelle.

*sign*<br/>
Zeiger auf den gespeicherten Zeichen-Indikator.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich. Der Rückgabewert ist ein Fehlercode, wenn ein Fehler auftritt. Fehlercodes sind in Errno.h definiert. Eine Liste dieser Fehler finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Bei einem in der folgenden Tabelle enthaltenen ungültigen Parameter wird von dieser Funktion der Handler für ungültige Parameter aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, um den Vorgang fortzusetzen, setzt diese Funktion **Errno** zu **EINVAL** und gibt **EINVAL**.

### <a name="error-conditions"></a>Fehlerbedingungen

|*buffer*|*sizeInBytes*|Wert|count|dec|sign|Zurück|Wert in *Puffer*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**NULL**|any|any|any|any|any|**EINVAL**|Nicht geändert.|
|Nicht **NULL** (zeigt auf gültigen Speicher)|<=0|any|any|any|any|**EINVAL**|Nicht geändert.|
|any|any|any|any|**NULL**|any|**EINVAL**|Nicht geändert.|
|any|any|any|any|any|**NULL**|**EINVAL**|Nicht geändert.|

## <a name="security-issues"></a>Sicherheitsprobleme

**_fcvt_s** kann eine zugriffsverletzung erzeugen, wenn *Puffer* nicht auf gültigen Speicher verweist und nicht **NULL**.

## <a name="remarks"></a>Hinweise

Die **_fcvt_s** -Funktion konvertiert eine Gleitkommazahl in eine Null-terminierte Zeichenfolge. Die *Wert* -Parameter ist die zu konvertierende Gleitkommazahl. **_fcvt_s** speichert die Ziffern von *Wert* als Zeichenfolge und fügt ein Null-Zeichen ('\0'). Die *Anzahl* Parameter gibt die Anzahl der Ziffern nach dem Dezimaltrennzeichen gespeichert werden. Überschüssige Ziffern werden gerundet, *Anzahl* platziert. Wenn weniger als *Anzahl* Dezimalstellen, die Zeichenfolge mit Nullen aufgefüllt.

In der Zeichenfolge werden nur Ziffern gespeichert. Die Position der Dezimalstelle und das Vorzeichen des *Wert* erhalten *Dec* und *anmelden* nach dem Aufruf. Die *Dec* Parameter verweist auf einen ganzzahligen Wert; dieser ganzzahlige Wert gibt die Position der Dezimalstelle im Verhältnis der Anfang der Zeichenfolge. Der Wert null oder ein negativer ganzzahliger Wert geben an, dass sich die Dezimalstelle links neben der ersten Ziffer befindet. Der Parameter *anmelden* verweist auf eine ganze Zahl, der das Vorzeichen *Wert*. Die ganze Zahl auf 0 festgelegt ist, wenn *Wert* positiv ausfällt und wird festgelegt, auf eine Zahl ungleich NULL, wenn *Wert* ist negativ.

Ein Puffer der Länge **_CVTBUFSIZE** reicht für alle Gleitkommawerte Wert.

Der Unterschied zwischen **_ecvt_s** und **_fcvt_s** befindet sich in die Interpretation der *Anzahl* Parameter. **_ecvt_s** interpretiert *Anzahl* als die Gesamtanzahl von Ziffern in der Ausgabezeichenfolge und **_fcvt_s** interpretiert *Anzahl* als die Anzahl der Ziffern nach dem Dezimaltrennzeichen an.

Die Verwendung dieser Funktion in C++ wird durch eine Vorlagenüberladung vereinfacht. Eine Überladung kann automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Die Debugversion dieser Funktion füllt zunächst den Puffer mit „0xFD“ auf. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|Optionaler Header|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

**Bibliotheken:** Alle Versionen der [CRT-Bibliotheksfunktionen](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// fcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_fcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 120000
```

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
