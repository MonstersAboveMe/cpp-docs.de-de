---
title: _vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l
ms.date: 11/04/2016
apiname:
- _vsprintf_p
- _vswprintf_p
- _vsprintf_p_l
- _vswprintf_p_l
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
apitype: DLLExport
f1_keywords:
- vsprintf_p
- _vswprintf_p
- _vstprintf_p
- vswprintf_p
- _vsprintf_p
- vstprintf_p
helpviewer_keywords:
- vstprintf_p_l function
- _vsprintf_p_l function
- _vstprintf_p function
- vsprintf_p_l function
- _vswprintf_p function
- vswprintf_p function
- vsprintf_p function
- vswprintf_p_l function
- _vswprintf_p_l function
- vstprintf_p function
- formatted text [C++]
- _vsprintf_p function
- _vstprintf_p_l function
ms.assetid: 00821c0d-9fee-4d8a-836c-0669cfb11317
ms.openlocfilehash: 15f368da84eb9cbf8c394a0e9b5eeec2611c3f7f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383437"
---
# <a name="vsprintfp-vsprintfpl-vswprintfp-vswprintfpl"></a>_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l

Schreibt mithilfe eines Zeigers auf eine Liste von Argumenten eine formatierte Ausgabe mit der Möglichkeit, die Reihenfolge anzugeben, in der die Argumente verwendet werden.

## <a name="syntax"></a>Syntax

```C
int _vsprintf_p(
   char *buffer,
   size_t sizeInBytes,
   const char *format,
   va_list argptr
);
int _vsprintf_p_l(
   char *buffer,
   size_t sizeInBytes,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vswprintf_p(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vswprintf_p_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Parameter

*buffer*<br/>
Speicherort für die Ausgabe.

*sizeInBytes*<br/>
Größe des *Puffer* in Zeichen.

*count*<br/>
Maximale Anzahl, der in der Unicode-Version dieser Funktion zu speichernden Zeichen.

*format*<br/>
Formatangabe.

*argptr*<br/>
Zeiger zur Liste der Argumente.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**_vsprintf_p** und **_vswprintf_p** Zurückgeben der Anzahl der geschriebenen Zeichen nicht einschließlich des abschließenden Zeichens Null oder ein negativer Wert, wenn ein Ausgabefehler auftritt.

## <a name="remarks"></a>Hinweise

Jede dieser Funktionen verwendet einen Zeiger auf eine Argumentliste und formatiert und schreibt die angegebenen Daten in den Speicher verweist *Puffer*.

Diese Funktionen unterscheiden sich von der **Vsprintf_s** und **Vswprintf_s** nur darin, dass sie Positionsparameter unterstützen. Weitere Informationen finden Sie unter [printf-Positionsparameter](../../c-runtime-library/printf-p-positional-parameters.md).

Die Versionen dieser Funktionen mit den **_l** -Suffix sind beinahe identisch, außer dass sie den übergebenen Gebietsschemaparameter anstelle des aktuellen threadgebietsschemas Locale-Parameter verwenden.

Wenn die *Puffer* oder *Format* Parameter sind **NULL** Zeigern, wenn die Anzahl Null ist, ist oder wenn Formatzeichenfolge ungültige Formatierung enthält Zeichen, die ungültigen Parameter Handler wird aufgerufen, wie in beschrieben [Parametervalidierung](../../c-runtime-library/parameter-validation.md). Wenn die weitere Ausführung zugelassen wird, um den Vorgang fortzusetzen, die Funktionen-1 zurück und legen Sie **Errno** zu **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstprintf_p**|**_vsprintf_p**|**_vsprintf_p**|**_vswprintf_p**|
|**_vstprintf_p_l**|**_vsprintf_p_l**|**_vsprintf_p_l**|**_vswprintf_p_l**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|Optionale Header|
|-------------|---------------------|----------------------|
|**_vsprintf_p**, **_vsprintf_p_l**|\<stdio.h> und \<stdarg.h>|\<varargs.h>*|
|**_vswprintf_p**, **_vswprintf_p_l**|\<stdio.h> oder \<wchar.h> und \<stdarg.h>|\<varargs.h>*|

\* Benötigt für die Kompatibilität mit UNIX V.

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt__vsprintf_p.c
// This program uses vsprintf_p to write to a buffer.
// The size of the buffer is determined by _vscprintf_p.

#include <stdlib.h>
#include <stdio.h>
#include <stdarg.h>

void example( char * format, ... )
{
    va_list  args;
    int      len;
    char     *buffer = NULL;

    va_start( args, format );

    // _vscprintf doesn't count the
    // null terminating string so we add 1.
    len = _vscprintf_p( format, args ) + 1;

    // Allocate memory for our buffer
    buffer = (char*)malloc( len * sizeof(char) );
    if (buffer)
    {
        _vsprintf_p( buffer, len, format, args );
        puts( buffer );
        free( buffer );
    }
    va_end( args );
}

int main( void )
{
    // First example
    example( "%2$d %1$c %3$d", '<', 123, 456 );

    // Second example
    example( "%s", "This is a string" );
}
```

```Output
123 < 456
This is a string
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf-Funktionen](../../c-runtime-library/vprintf-functions.md)<br/>
[Syntax der Formatangabe: printf- und wprintf-Funktionen](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
