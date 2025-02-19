---
title: memmove, wmemmove
ms.date: 11/04/2016
apiname:
- memmove
- wmemmove
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- memmove
- wmemmove
helpviewer_keywords:
- wmemmove function
- memmove function
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
ms.openlocfilehash: 988af1c2678e20ea40ce4dfe331a3b6c49db0547
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156563"
---
# <a name="memmove-wmemmove"></a>memmove, wmemmove

Verschiebt einen Puffer in einen anderen. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [memmove_s, wmemmove_s](memmove-s-wmemmove-s.md).

## <a name="syntax"></a>Syntax

```C
void *memmove(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemmove(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parameter

*dest*<br/>
Zielobjekt.

*src*<br/>
Quellobjekt.

*count*<br/>
Anzahl von Bytes (**Memmove**) oder Zeichen (**Wmemmove**) zu kopieren.

## <a name="return-value"></a>Rückgabewert

Der Wert des *Dest*.

## <a name="remarks"></a>Hinweise

Kopien *Anzahl* Bytes (**Memmove**) oder Zeichen (**Wmemmove**) von *Src* zu *Dest*. Wenn einige Bereiche des Quell- und des Zielbereichs überlappen, stellen beide Funktionen sicher, dass die ursprünglichen Quellbytes im überlappenden Bereich kopiert werden, bevor es sie überschreibt.

**Sicherheitshinweis** Stellen Sie sicher, dass der Zielpuffer dieselbe Größe wie der Quellpuffer aufweist bzw. größer ist. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/desktop/SecBP/avoiding-buffer-overruns).

Die **Memmove** und **Wmemmove** Funktionen sind nur veraltet, wenn die Konstante **_CRT_SECURE_DEPRECATE_MEMORY** vor der inklusionsanweisung für nacheinander definiert ist die Funktionen werden als veraltet markierte, z. B. wie im folgenden Beispiel:

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <string.h>
```

oder

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**memmove**|\<string.h>|
|**wmemmove**|\<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_memcpy.c
// Illustrate overlapping copy: memmove
// always handles it correctly; memcpy may handle
// it correctly.
//

#include <memory.h>
#include <string.h>
#include <stdio.h>

char str1[7] = "aabbcc";

int main( void )
{
   printf( "The string: %s\n", str1 );
   memcpy( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );

   strcpy_s( str1, sizeof(str1), "aabbcc" );   // reset string

   printf( "The string: %s\n", str1 );
   memmove( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );
}
```

```Output
The string: aabbcc
New string: aaaabb
The string: aabbcc
New string: aaaabb
```

## <a name="see-also"></a>Siehe auch

[Pufferbearbeitung](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
