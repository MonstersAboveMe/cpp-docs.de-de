---
title: _aligned_malloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_malloc_dbg
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
- _aligned_malloc_dbg
- aligned_malloc_dbg
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
ms.openlocfilehash: eb58313c892ffe13e9f8e34e98b7940022899d14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341638"
---
# <a name="alignedmallocdbg"></a>_aligned_malloc_dbg

Belegt einen Speicherblock in einer angegebenen Ausrichtungsgrenze mit zusätzlichem Speicherplatz für einen Debugheader und Überschreibungspuffer (nur Debugversion).

## <a name="syntax"></a>Syntax

```C
void * _aligned_malloc_dbg(
    size_t size,
    size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parameter

*size*<br/>
Größe der angeforderten Speicherzuweisung.

*alignment*<br/>
Der Ausrichtungswert, der eine ganzzahlige Potenz von 2 sein muss.

*filename*<br/>
Zeiger zum Namen der Quelldatei, der die Belegung angefordert hat, oder NULL.

*linenumber*<br/>
Zeilennummer in der Quelldatei, in der die Belegung angefordert wurde, oder NULL.

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Speicherblock, der zugewiesen wurde oder NULL, wenn der Vorgang fehlgeschlagen ist.

## <a name="remarks"></a>Hinweise

**_aligned_malloc_dbg** ist eine Debugversion von der [_aligned_malloc](aligned-malloc.md) Funktion. Wenn [_DEBUG](../../c-runtime-library/debug.md) nicht definiert ist, jeden Aufruf von **_aligned_malloc_dbg** wird nach einer Verkleinerung auf einen Aufruf von `_aligned_malloc`. Beide `_aligned_malloc` und **_aligned_malloc_dbg** belegen einen Speicherblock im Basisheap, jedoch **_aligned_malloc_dbg** bietet mehrere Debugfunktionen: Puffer auf beiden Seiten des benutzerteils des der Blocks zum Prüfen auf Speicherverluste, und *Filename*/*Linenumber* Informationen zum Ermitteln des Ursprungs von belegungsanforderungen. Nachverfolgen von bestimmten belegungstypen mit einem blocktypparameter ist kein unterstützten Debug-Feature für ausgerichtete Zuweisungen. Ausgerichtete Zuweisungen werden als ein _NORMAL_BLOCK-Block-Typ angezeigt.

**_aligned_malloc_dbg** belegt den Speicherblock mit etwas mehr Speicherplatz als der angeforderten *Größe*. Der zusätzliche Speicherplatz wird vom Debugheapmanager verwendet, um die Debugspeicherblöck zu verknüpfen und Debugheaderinformationen und Überschreibungspuffer für die Anwendung bereitzustellen. Wenn der Block belegt wurde, wird der Benutzerteil des Blocks mit dem Wert "0xCD" gefüllt, und jeder der Überschreibungspuffer wird mit "0xFD" gefüllt.

**_aligned_malloc_dbg** legt `errno` zu `ENOMEM` , wenn eine speicherbelegung fehlschlägt oder die Menge an Speicherplatz (einschließlich der bereits erwähnten Mehraufwands) überschreitet `_HEAP_MAXREQ`. Informationen hierzu und über andere Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Darüber hinaus **_aligned_malloc_dbg** überprüft die eigenen Parameter. Wenn *Ausrichtung* ist keine Potenz von 2 oder *Größe* NULL ist, ruft diese Funktion den Handler für ungültige Parameter aus, wie in beschrieben [Parametervalidierung](../../c-runtime-library/parameter-validation.md). Wenn die weitere Ausführung zugelassen wird, um den Vorgang fortzusetzen, diese Funktion gibt NULL zurück und legt `errno` zu `EINVAL`.

Informationen darüber, wie Speicherblöcke in der Debugversion des Basisheaps zugeordnet, initialisiert und verwaltet werden, finden Sie unter [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Informationen zu den Belegungsblocktypen und ihrer Verwendung finden Sie unter [Blocktypen auf dem Debugheap](/visualstudio/debugger/crt-debug-heap-details). Weitere Informationen zu den Unterschieden zwischen dem Aufruf einer Standardheapfunktion und ihrer Debugversion in einem Debugbuild einer Anwendung finden Sie unter [Debugversionen von Heapbelegungsfunktionen](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_aligned_malloc_dbg**|\<crtdbg.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Nur Debugversionen der [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Siehe auch

[Debugroutinen](../../c-runtime-library/debug-routines.md)