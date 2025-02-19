---
title: _fdopen, _wfdopen
ms.date: 12/12/2017
apiname:
- _fdopen
- _wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
ms.openlocfilehash: 0cde110bf1dd12c23a6b0b658809502743d9edd3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334774"
---
# <a name="fdopen-wfdopen"></a>_fdopen, _wfdopen

Verknüpft einen Stream mit einer Datei, die zuvor für E/A auf niedriger Ebene geöffnet war.

## <a name="syntax"></a>Syntax

```C
FILE *_fdopen(
   int fd,
   const char *mode
);
FILE *_wfdopen(
   int fd,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parameter

*fd*<br/>
Dateideskriptor der geöffneten Datei.

*mode*<br/>
Der Typ des Dateizugriffs.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Zeiger auf den geöffneten Stream zurück. Ein NULL-Zeigerwert gibt einen Fehler an. Wenn ein Fehler auftritt, wird der ungültige Parameterhandler aufgerufen, so wie dies unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben wird. Wenn die weitere Ausführung zugelassen wird, um den Vorgang fortzusetzen, **Errno** entweder auf festgelegt ist **EBADF**, das angibt, dass eines fehlerhafter Dateideskriptor, oder **EINVAL**, die angibt, dass *Modus*  wurde ein null-Zeiger.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **_fdopen** Funktion verknüpft einen e/a-Stream mit der Datei, die durch identifiziert wird *fd*, und daher kann eine Datei, die geöffnet wird, für Low-Level e/a, gepuffert und formatiert werden. **_wfdopen** ist eine Breitzeichen-Version von **_fdopen**; die *Modus* Argument **_wfdopen** ist eine Breitzeichen-Zeichenfolge. **_wfdopen** und **_fdopen** Verhalten sich andernfalls identisch.

Dateideskriptoren übergebenen **_fdopen** gehören mit dem zurückgegebenen **Datei &#42;**  Stream. Wenn **_fdopen** erfolgreich ist, rufen Sie keine [ \_schließen](close.md) auf den Dateideskriptor. Aufrufen von [Fclose](fclose-fcloseall.md) für das zurückgegebene **Datei &#42;**  schließt auch den Dateideskriptor.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|\_UNICODE und \_MBCS nicht definiert|\_MBCS definiert|\_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

Die *Modus* Zeichenfolge gibt den Typ des Dateizugriffs, die für die Datei angeforderten:

| *mode* | Zugriff |
|--------|--------|
| **"r"** | Öffnet zum Lesen. Wenn die Datei nicht vorhanden ist oder wurde nicht gefunden, die **Fopen** -Aufruf fehl. |
| **"w"** | Öffnet eine leere Datei zum Schreiben. Wenn die angegebene Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **„a“** | Öffnet zum Schreiben am Ende der Datei (Anfügen). Erstellt die Datei, wenn sie nicht vorhanden ist. |
| **„r+“** | Öffnet sowohl zum Lesen als auch zum Schreiben. Die Datei muss vorhanden sein. |
| **„w+“** | Öffnet eine leere Datei zum Lesen und Schreiben. Wenn die Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **„a+“** | Öffnet sich zum Lesen und Anfügen. Erstellt die Datei, wenn sie nicht vorhanden ist. |

Wenn eine Datei geöffnet wird, mit der **"a"** oder **"a +"** Zugriffstyp am Ende der Datei erfolgen alle Schreibvorgänge. Der Dateizeiger kann mit [Fseek](fseek-fseeki64.md) oder [rewind](rewind.md), er wird jedoch immer verschoben zurück an das Ende der Datei, bevor ein Schreibvorgang durchgeführt wird. Folglich können vorhandene Daten nicht überschrieben werden. Wenn die **"R +"**, **"w +"**, oder **"a +"** angegeben wird, sind Lese- und Schreibvorgänge zulässig (die Datei gilt als für "Update" geöffnet). Aber wenn Sie zwischen Lesen und Schreiben wechseln, muss vorhanden sein einen dazwischen liegenden [Fflush](fflush.md), [Fsetpos](fsetpos.md), [Fseek](fseek-fseeki64.md), oder [rewind](rewind.md) der Vorgang. Sie können angeben, dass die aktuelle Position für die [Fsetpos](fsetpos.md) oder [Fseek](fseek-fseeki64.md) -Operation, wenn Sie möchten.

Zusätzlich zu den obigen Werten können die folgenden Zeichen enthalten sein *Modus* um den Übersetzungsmodus für Zeilenumbruchzeichen anzugeben:

| *Modus* Modifizierer | Verhalten |
|-----------------|----------|
| **t** | Öffnen im Textmodus (übersetzt). Im Textmodus werden Wagenrücklauf-/Zeilenvorschub-Kombinationen (CR-LF) bei der Eingabe in einzelne Zeilenvorschübe (LF) übersetzt. LF-Zeichen werden bei der Ausgabe in CR-LF-Kombinationen übersetzt. Außerdem wird STRG+Z bei der Eingabe als EOF-Zeichen interpretiert. |
| **b** | Wird im binären (nicht übersetzten) Modus geöffnet. Übersetzungen aus **t** -Modus werden unterdrückt. |
| **c** | Aktivieren Sie das commitflag für den zugeordneten *Filename* , damit der Inhalt des Dateipuffers direkt, wenn entweder auf den Datenträger geschrieben werden **Fflush** oder **_flushall** aufgerufen wird. |
| **n** | Zurücksetzen der Commit-Flag für das zugeordnete *Filename* auf "No-Commit". Dies ist die Standardeinstellung. Dabei wird auch das globale Commitflag überschrieben, wenn Sie das Programm mit „Commode.obj“ verknüpfen. Der Standardwert des globalen Commitflags lautet „no-commit“, es sei denn, Sie verknüpfen das Programm explizit mit „Commode.obj“. |

Die **t**, **c**, und **n** *Modus* Optionen sind Microsoft-Erweiterungen für **Fopen** und **_fdopen**. Verwenden Sie sie nicht, wenn Sie die ANSI-Portabilität beibehalten möchten.

Wenn **t** oder **b** nicht erhält, *Modus*, wird der standardübersetzungsmodus durch die globale Variable definiert [ \_Fmode](../../c-runtime-library/fmode.md). Wenn **t** oder **b** das Argument, schlägt die Funktion vorangestellt ist, und gibt NULL zurück. Eine Erörterung von Text- und Binärmodi finden Sie unter [Text- und Binärmodus-Datei-E/A](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Gültige Zeichen für die *Modus* in verwendete Zeichenfolge **Fopen** und **_fdopen** entsprechen *Oflag* verwendeten Argumenten [ \_öffnen](open-wopen.md) und [ \_Sopen](sopen-wsopen.md), wie in dieser Tabelle dargestellt:

|Zeichen in *Modus* Zeichenfolge|Entsprechende *Oflag* Wert für **_open** und **_sopen**|
|---------------------------------|---------------------------------------------------|
|**a**|**\_O\_WRONLY &#124; \_O\_APPEND** (in der Regel  **\_O\_WRONLY &#124; \_O\_erstellen &#124; \_O \_APPEND**)|
|**a+**|**\_O\_RDWR &#124; \_O\_APPEND** (in der Regel  **\_O\_RDWR &#124; \_O\_APPEND &#124; \_O\_ CREAT** )|
|**r**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (usually **\_O\_WRONLY &#124; \_O\_CREAT &#124; \_O\_TRUNC**)|
|**w+**|**\_O\_RDWR** (usually **\_O\_RDWR &#124; \_O\_CREAT &#124; \_O\_TRUNC**)|
|**b**|**\_O\_BINÄRE**|
|**t**|**\_O\_TEXT**|
|**c**|Keiner|
|**n**|Keiner|

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```c
// crt_fdopen.c
// This program opens a file by using low-level
// I/O, then uses _fdopen to switch to stream
// access. It counts the lines in the file.

#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>
#include <share.h>

int main( void )
{
   FILE *stream;
   int  fd, count = 0;
   char inbuf[128];

   // Open a file.
   if( _sopen_s( &fd, "crt_fdopen.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
      exit( 1 );

   // Get stream from file descriptor.
   if( (stream = _fdopen( fd, "r" )) == NULL )
      exit( 1 );

   while( fgets( inbuf, 128, stream ) != NULL )
      count++;

   // After _fdopen, close by using fclose, not _close.
   fclose( stream );
   printf( "Lines in file: %d\n", count );
}
```

### <a name="input-crtfdopentxt"></a>Eingabe: crt_fdopen.txt

```Input
Line one
Line two
```

### <a name="output"></a>Output

```Output
Lines in file: 2
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[\_dup, \_dup2](dup-dup2.md)<br/>
[fclose, \_fcloseall](fclose-fcloseall.md)<br/>
[fopen, \_wfopen](fopen-wfopen.md)<br/>
[freopen, \_wfreopen](freopen-wfreopen.md)<br/>
[\_Öffnen von \_Wopen](open-wopen.md)<br/>
