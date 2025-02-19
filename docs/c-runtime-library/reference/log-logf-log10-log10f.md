---
title: log, logf, logl, log10, log10f, log10l
ms.date: 04/05/2018
apiname:
- log10f
- logf
- log10
- log
- log10l
- logl
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
- logf
- logl
- _log10l
- log
- _logl
- log10f
- log10l
- log10
helpviewer_keywords:
- calculating logarithms
- log10f function
- log10 function
- log function
- log10l function
- logl function
- logf function
- logarithms
ms.assetid: 7adc77c2-04f7-4245-a980-21215563cfae
ms.openlocfilehash: c8e3f73e61fefa7a39a6d53d63739b094d78c499
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62286011"
---
# <a name="log-logf-logl-log10-log10f-log10l"></a>log, logf, logl, log10, log10f, log10l

Berechnet die Logarithmen.

## <a name="syntax"></a>Syntax

```C
double log( double x );
float logf( float x );
long double logl( double x );
double log10( double x );
float log10f ( float x );
long double log10l( double x );
```

```cpp
float log( float x );  // C++ only
long double log( long double x );  // C++ only
float log10( float x );  // C++ only
long double log10( long double x );  // C++ only
```

### <a name="parameters"></a>Parameter

*w*<br/>
Ein Wert, dessen Logarithmus gesucht wird.

## <a name="return-value"></a>Rückgabewert

Die **Log** Funktionen geben den natürlichen Logarithmus (Basis *e*) der *x* bei erfolgreicher Ausführung. Die **log10** Funktionen geben den Logarithmus zur Basis-10 zurück. Wenn *x* ist negativ, diese Funktionen ein unbestimmtes (Suchen), geben standardmäßig zurück. Wenn *x* gleich 0 ist, geben sie die unendlich (INF) zurück.

|Eingabe|SEH-Ausnahme|Matherr-Ausnahme|
|-----------|-------------------|-----------------------|
|± QNAN, IND|none|_DOMAIN|
|± 0|ZERODIVIDE|_SING|
|*x* < 0|INVALID|_DOMAIN|

**Log** und **log10** eine Implementierung, Streaming SIMD Extensions 2 (SSE2) verwendet, haben. Informationen und Einschränkungen zur Verwendung der SSE2-Implementierung finden Sie unter [_set_SSE2_enable](set-sse2-enable.md).

## <a name="remarks"></a>Hinweise

Da C++ das Überladen zulässt, können Sie Überladungen von aufrufen können **Log** und **log10** verwenden und zurückgeben **"float"** oder **long double** Werte. In einem C-Programm **Log** und **log10** immer annehmen und Zurückgeben einer **doppelte**.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**log**, **logf**, **logl**, **log10**, **log10f**, **log10l**|\<math.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_log.c
/* This program uses log and log10
* to calculate the natural logarithm and
* the base-10 logarithm of 9,000.
*/

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 9000.0;
   double y;

   y = log( x );
   printf( "log( %.2f ) = %f\n", x, y );
   y = log10( x );
   printf( "log10( %.2f ) = %f\n", x, y );
}
```

```Output
log( 9000.00 ) = 9.104980
log10( 9000.00 ) = 3.954243
```

Verwenden Sie zum Generieren von Logarithmen für anderen Basen die mathematische Beziehung: Logarithmische Basis b von a = Natürlicher Logarithmus (a) / Natürlicher Logarithmus (b).

```cpp
// logbase.cpp
#include <math.h>
#include <stdio.h>

double logbase(double a, double base)
{
   return log(a) / log(base);
}

int main()
{
   double x = 65536;
   double result;

   result = logbase(x, 2);
   printf("Log base 2 of %lf is %lf\n", x, result);
}
```

```Output
Log base 2 of 65536.000000 is 16.000000
```

## <a name="see-also"></a>Siehe auch

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[_matherr](matherr.md) <br/>
[pow, powf, powl](pow-powf-powl.md) <br/>
[_CIlog](../../c-runtime-library/cilog.md) <br/>
[_CIlog10](../../c-runtime-library/cilog10.md)<br/>
