---
title: tmpfile_s
ms.date: 11/04/2016
apiname:
- tmpfile_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 341e1c8ed6dd20ec7e6a3d71999fb365e45e614a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155575"
---
# <a name="tmpfiles"></a>tmpfile_s

Erstellt eine temporäre Datei. Dies ist eine Version von [tmpfile](tmpfile.md) mit Sicherheitserweiterungen wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t tmpfile_s(
   FILE** pFilePtr
);
```

### <a name="parameters"></a>Parameter

*pFilePtr*<br/>
Die Adresse eines Zeigers, um die Adresse des generierten Zeigers in einen Stream zu speichern.

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg 0 (null) zurück und einen Fehlercode, wenn ein Fehler auftritt.

### <a name="error-conditions"></a>Fehlerbedingungen

|*pFilePtr*|**Rückgabewert**|**Inhalt der***pFilePtr*|
|----------------|----------------------|---------------------------------|
|**NULL**|**EINVAL**|nicht geändert|

Wenn der obengenannte Parametervalidierungsfehler auftritt, wird der ungültige Parameterhandler wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben aufgerufen. Wenn die weitere Ausführung zugelassen wird, um den Vorgang fortzusetzen, **Errno** nastaven NA hodnotu **EINVAL** und der Rückgabewert ist **EINVAL**.

## <a name="remarks"></a>Hinweise

Die **Tmpfile_s** -Funktion erstellt eine temporäre Datei und fügt einen Zeiger auf diesen Datenstrom in die *pFilePtr* Argument. Die temporäre Datei wird im Stammverzeichnis erstellt. Verwenden Sie zum Erstellen einer temporären Datei in einem anderen Verzeichnis als dem Stammverzeichnis [tmpnam_s](tmpnam-s-wtmpnam-s.md) oder [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) in Verbindung mit [fopen](fopen-wfopen.md).

Wenn die Datei kann nicht geöffnet werden, **Tmpfile_s** schreibt **NULL** auf die *pFilePtr* Parameter. Diese temporäre Datei wird automatisch gelöscht, wenn die Datei geschlossen wird, wenn das Programm beendet, normalerweise, oder wenn wird, **_rmtmp** aufgerufen wird, unter der Annahme, dass das aktuelle Arbeitsverzeichnis nicht ändert. Die temporäre Datei wird geöffnet, **w + b** (binären Lese-/Schreib-) Modus.

Fehler kann auftreten, wenn Sie versuchen, mehr als **TMP_MAX_S** (Siehe STDIO. H) Aufrufe mit **Tmpfile_s**.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

> [!NOTE]
> In diesem Beispiel wird möglicherweise über Administratorrechte auf dem Windows ausgeführt.

```C
// crt_tmpfile_s.c
// This program uses tmpfile_s to create a
// temporary file, then deletes this file with _rmtmp.
//

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char tempstring[] = "String to be written";
   int  i;
   errno_t err;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      err = tmpfile_s(&stream);
      if( err )
         perror( "Could not open new temporary file\n" );
      else
         printf( "Temporary file %d was created\n", i );
   }

   // Remove temporary files.
   printf( "%d temporary files deleted\n", _rmtmp() );
}
```

```Output
Temporary file 1 was created
Temporary file 2 was created
Temporary file 3 was created
3 temporary files deleted
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
