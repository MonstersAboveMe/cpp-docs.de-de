---
title: _lrotl, _lrotr
ms.date: 04/04/2018
apiname:
- _lrotl
- _lrotr
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- lrotr
- lrotl
- _lrotr
- _lrotl
helpviewer_keywords:
- lrotl function
- bits
- _lrotr function
- lrotr function
- rotating bits
- _lrotl function
- bits, rotating
ms.assetid: d42f295b-35f9-49d2-9ee4-c66896ffe68e
ms.openlocfilehash: 71ca61676e4551155f9f14e792c5c1cee65ddb7e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156966"
---
# <a name="lrotl-lrotr"></a>_lrotl, _lrotr

Rotiert Bits nach links (**_lrotl**) oder rechts (**_lrotr**).

## <a name="syntax"></a>Syntax

```C
unsigned long _lrotl( unsigned long value, int shift );
unsigned long _lrotr( unsigned long value, int shift );
```

### <a name="parameters"></a>Parameter

*value*<br/>
Der zu rotierende Wert.

*shift*<br/>
Die Anzahl von Bits, die den *Wert* verschieben.

## <a name="return-value"></a>Rückgabewert

Beide Funktionen geben den rotierten Wert zurück. Es gibt keine Fehlerrückgabe.

## <a name="remarks"></a>Hinweise

Die **_lrotl** und **_lrotr** Funktionen Drehen *Wert* von *UMSCHALT* Bits. **_lrotl** rotiert den Wert nach links, auf mehr signifikante Bits. **_lrotr** rotiert den Wert nach rechts, für weniger signifikante Bits. Beide Funktionen umschließen Bits, die von einem Ende des *value* zum anderen Ende rotieren.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_lrotl**, **_lrotr**|\<stdlib.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_lrot.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   unsigned long val = 0x0fac35791;

   printf( "0x%8.8lx rotated left eight bits is 0x%8.8lx\n",
            val, _lrotl( val, 8 ) );
   printf( "0x%8.8lx rotated right four bits is 0x%8.8lx\n",
            val, _lrotr( val, 4 ) );
}
```

```Output
0xfac35791 rotated left eight bits is 0xc35791fa
0xfac35791 rotated right four bits is 0x1fac3579
```

## <a name="see-also"></a>Siehe auch

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[_rotl, _rotl64, _rotr, _rotr64](rotl-rotl64-rotr-rotr64.md)<br/>
