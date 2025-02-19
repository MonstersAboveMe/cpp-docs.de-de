---
title: _chmod, _wchmod
ms.date: 11/04/2016
apiname:
- _chmod
- _wchmod
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _chmod
- _wchmod
- wchmod
helpviewer_keywords:
- _chmod function
- wchmod function
- file permissions [C++]
- chmod function
- files [C++], changing permissions
- _wchmod function
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
ms.openlocfilehash: 278ee1e6dda9e153b55676ce5c0ca389f383efd1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348470"
---
# <a name="chmod-wchmod"></a>_chmod, _wchmod

Ändert die Dateiberechtigungseinstellungen.

## <a name="syntax"></a>Syntax

```C
int _chmod( const char *filename, int pmode );
int _wchmod( const wchar_t *filename, int pmode );
```

### <a name="parameters"></a>Parameter

*filename*<br/>
Name der vorhandenen Datei.

*pmode*<br/>
Berechtigungseinstellung für die Datei.

## <a name="return-value"></a>Rückgabewert

Diese Funktionen geben 0 zurück, wenn die Berechtigungseinstellung erfolgreich geändert wurde. Ein Rückgabewert 1 gibt Fehler an. Wenn die angegebene Datei nicht gefunden werden konnte, **Errno** nastaven NA hodnotu **ENOENT**; Wenn ein Parameter ungültig ist, ist **Errno** nastaven NA hodnotu **EINVAL**.

## <a name="remarks"></a>Hinweise

Die **_chmod** -Funktion ändert die berechtigungseinstellung der Datei anhand des *Filename*. Die Berechtigungseinstellung steuert den Lese- und Schreibzugriff auf die Datei. Der ganzzahlige Ausdruck *Pmode* enthält eine oder beide der folgenden Manifestkonstanten, die in sys\stat definiert.

| *pmode* | Bedeutung |
|-|-|
| **\_S\_IREAD** | Nur Lesen zugelassen. |
| **\_S\_IWRITE** | Schreiben zugelassen. (Lässt tatsächlich Lesen und Schreiben zu.) |
| **\_S\_IREAD** &#124; **\_S\_IWRITE** | Lesen und Schreiben erlaubt. |

Wenn beide Konstanten gegeben sind, werden sie verknüpft, mit dem bitweisen or -Operator (**\|**). Wenn keine Schreibberechtigung gewährt wird, kann die Datei nur gelesen werden. Hinweis: Alle Dateien sind stets lesbar; es ist nicht möglich, nur Schreibberechtigungen zu vergeben. Deshalb sind die Modi **_S_IWRITE** und **_S_IREAD** \| **_S_IWRITE** entsprechen.

**_wchmod** ist eine Breitzeichen-Version von **_chmod**; die *Filename* Argument **_wchmod** ist eine Breitzeichen-Zeichenfolge. **_wchmod** und **_chmod** Verhalten sich andernfalls identisch.

Diese Funktion überprüft ihre Parameter. Wenn *Pmode* keine Kombination aus einer der Manifestkonstanten ist oder enthält eine Alternative Gruppe von Konstanten, die Funktion einfach ignoriert diese. Wenn *Filename* ist **NULL**, Handler für ungültige Parameter aufgerufen, siehe [Parametervalidierung](../../c-runtime-library/parameter-validation.md). Wenn die weitere Ausführung zugelassen wird, um den Vorgang fortzusetzen, **Errno** nastaven NA hodnotu **EINVAL** und die Funktion gibt-1 zurück.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod**|**_chmod**|**_wchmod**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_chmod**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wchmod**|\<io.h> oder \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_chmod.c
// This program uses _chmod to
// change the mode of a file to read-only.
// It then attempts to modify the file.
//

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

// Change the mode and report error or success
void set_mode_and_report(char * filename, int mask)
{
   // Check for failure
   if( _chmod( filename, mask ) == -1 )
   {
      // Determine cause of failure and report.
      switch (errno)
      {
         case EINVAL:
            fprintf( stderr, "Invalid parameter to chmod.\n");
            break;
         case ENOENT:
            fprintf( stderr, "File %s not found\n", filename );
            break;
         default:
            // Should never be reached
            fprintf( stderr, "Unexpected error in chmod.\n" );
       }
   }
   else
   {
      if (mask == _S_IREAD)
        printf( "Mode set to read-only\n" );
      else if (mask & _S_IWRITE)
        printf( "Mode set to read/write\n" );
   }
   fflush(stderr);
}

int main( void )
{

   // Create or append to a file.
   system( "echo /* End of file */ >> crt_chmod.c_input" );

   // Set file mode to read-only:
   set_mode_and_report("crt_chmod.c_input ", _S_IREAD );

   system( "echo /* End of file */ >> crt_chmod.c_input " );

   // Change back to read/write:
   set_mode_and_report("crt_chmod.c_input ", _S_IWRITE );

   system( "echo /* End of file */ >> crt_chmod.c_input " );
}
```

```Output

A line of text.
```

```Output

      A line of text.Mode set to read-only
Access is denied.
Mode set to read/write
```

## <a name="see-also"></a>Siehe auch

[Dateibehandlung](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat- und _wstat-Funktionen](stat-functions.md)<br/>
