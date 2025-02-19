---
title: rand_s
ms.date: 1/02/2018
apiname:
- rand_s
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
- rand_s
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: d196a6f5d7483deb9a7e1b8d7fa929532b6197db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358124"
---
# <a name="rands"></a>rand_s

Generiert eine pseudozufällige Zahl. Dies ist eine sicherere Version der Funktion [Rand](rand.md), mit sicherheitsverbesserungen wie in beschrieben [Sicherheitsfunktionen in CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntax

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>Parameter

*randomValue*<br/>
Ein Zeiger auf eine ganze Zahl, die den generierten Wert enthalten soll.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, andernfalls ein Fehlercode. Wenn der eingegebene Zeiger _RandomValue_ ein null-Zeiger ist die Funktion ruft einen Handler für ungültige Parameter auf, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md). Wenn die weitere Ausführung zugelassen wird, gibt die Funktion **EINVAL** und **Errno** zu **EINVAL**. Wenn die Funktion, einem anderen Grund fehlschlägt *_RandomValue_ auf 0 festgelegt ist.

## <a name="remarks"></a>Hinweise

Die **Rand_s** Funktion schreibt eine pseudozufällige Ganzzahl im Bereich von 0 bis **UINT_MAX** , der eingegebene Zeiger. Die **Rand_s** Funktion verwendet das Betriebssystem kryptografisch sichere Zufallszahlen zu generieren. Wird nicht vom Ausgangswert verwendet die [Srand](srand.md) -Funktion, und beeinträchtigt die Zufallszahlensequenz von verwendeten [Rand](rand.md).

Die **Rand_s** -Funktion erfordert, dass die Konstante **_CRT_RAND_S** vor der inklusionsanweisung für die Funktion deklariert werden, wie im folgenden Beispiel definiert werden:

```C
#define _CRT_RAND_S
#include <stdlib.h>
```

**Rand_s** hängt von der [RtlGenRandom](/windows/desktop/api/ntsecapi/nf-ntsecapi-rtlgenrandom) -API, die nur in Windows XP und höher verfügbar ist.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**rand_s**|\<stdlib.h>|

Weitere Informationen finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_rand_s.c
// This program illustrates how to generate random
// integer or floating point numbers in a specified range.

// Remembering to define _CRT_RAND_S prior
// to inclusion statement.
#define _CRT_RAND_S

#include <stdlib.h>
#include <stdio.h>
#include <limits.h>

int main( void )
{
    int             i;
    unsigned int    number;
    double          max = 100.0;
    errno_t         err;

    // Display 10 random integers in the range [ 1,10 ].
    for( i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %u\n", (unsigned int) ((double)number /
                       ((double) UINT_MAX + 1 ) * 10.0) + 1);
    }

    printf_s("\n");

    // Display 10 random doubles in [0, max).
    for (i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %g\n", (double) number /
                          ((double) UINT_MAX + 1) * max );
    }
}
```

### <a name="sample-output"></a>Beispielausgabe

```Output
10
4
5
2
8
2
5
6
1
1

32.6617
29.4471
11.5413
6.41924
20.711
60.2878
61.0094
20.1222
80.9192
65.0712
```

## <a name="see-also"></a>Siehe auch

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
[srand](srand.md)<br/>
