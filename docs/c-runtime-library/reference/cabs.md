---
title: _cabs
ms.date: 11/04/2016
apiname:
- _cabs
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- cabsl
- _cabs
- _cabsl
helpviewer_keywords:
- cabs function
- cabsl function
- absolute values
- _cabsl function
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
ms.openlocfilehash: 3e95b6f568ce66b8e9e5483bd1dcbcfaa7af3d28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341066"
---
# <a name="cabs"></a>_cabs

Berechnet den absoluten Wert einer komplexen Zahl.

## <a name="syntax"></a>Syntax

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>Parameter

*z*<br/>
Komplexe Zahl.

## <a name="return-value"></a>Rückgabewert

**_cabs** gibt im Erfolgsfall den absoluten Wert des Arguments zurück. Bei einem Überlauf **_cabs** gibt **HUGE_VAL** und **Errno** zu **ERANGE**. Sie können die Fehlerbehandlung mit [_matherr](matherr.md) ändern.

## <a name="remarks"></a>Hinweise

Die **_cabs** -Funktion berechnet den absoluten Wert einer komplexen Zahl, die eine Struktur des Typs sein muss [_complex](../../c-runtime-library/standard-types.md). Die Struktur *z* besteht aus einer reellen Komponente *x* und einer imaginären Komponente *y*. Ein Aufruf von **_cabs** dieser Wert entspricht der Ausdruck `sqrt( z.x * z.x + z.y * z.y )`.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_cabs**|\<math.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_cabs.c
// Using _cabs, this program calculates
// the absolute value of a complex number.

#include <math.h>
#include <stdio.h>

int main( void )
{
   struct _complex number = { 3.0, 4.0 };
   double d;

   d = _cabs( number );
   printf( "The absolute value of %f + %fi is %f\n",
           number.x, number.y, d );
}
```

```Output
The absolute value of 3.000000 + 4.000000i is 5.000000
```

## <a name="see-also"></a>Siehe auch

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)