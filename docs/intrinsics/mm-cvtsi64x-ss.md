---
title: _mm_cvtsi64x_ss
ms.date: 11/04/2016
f1_keywords:
- _mm_cvtsi64x_ss
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
ms.openlocfilehash: 3ba9dc56cbb027e8cf9f31d293b3f96908aff5e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62264412"
---
# <a name="mmcvtsi64xss"></a>_mm_cvtsi64x_ss

**Microsoft-spezifisch**

Generiert die X64 erweiterte Version der Konvertieren von 64-Bit-Ganzzahl, mit einfacher Genauigkeit Floating-Point-Skalarwert (`cvtsi2ss`) Anweisung.

## <a name="syntax"></a>Syntax

```
__m128 _mm_cvtsi64x_ss(
   __m128 a,
   __int64 b
);
```

#### <a name="parameters"></a>Parameter

*a*<br/>
[in] Ein `__m128` Struktur, die vier Werte für Gleitkommazahlen mit einfacher Genauigkeit enthält.

*b*<br/>
[in] Eine 64-Bit-Ganzzahl in einen Gleitkommawert konvertiert werden soll.

## <a name="return-value"></a>Rückgabewert

Ein `__m128` -Struktur, deren erste Gleitkommawert das Ergebnis der Konvertierung ist. Die anderen drei Werte beim Übertragungsvorgang kopiert werden gegenüber `a`.

## <a name="requirements"></a>Anforderungen

|Systemintern|Architektur|
|---------------|------------------|
|`_mm_cvtsi64x_ss`|x64|

**Headerdatei** \<intrin.h >

## <a name="remarks"></a>Hinweise

Die `__m128` Werttypstruktur ein XMM-Register, sodass dieser systeminternen Funktion als Wert kann `b` registrieren im Systemspeicher in einer XMM verschoben werden soll.

Diese Routine ist nur als systeminterne Funktion verfügbar.

## <a name="example"></a>Beispiel

```
// _mm_cvtsi64x_ss.cpp
// processor: x64

#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtsi64x_ss)

int main()
{
    __m128 a;
    __int64 b = 54;

    a.m128_f32[0] = 0;
    a.m128_f32[1] = 0;
    a.m128_f32[2] = 0;
    a.m128_f32[3] = 0;
    a = _mm_cvtsi64x_ss(a, b);

    printf_s( "%lf %lf %lf %lf\n",
              a.m128_f32[0], a.m128_f32[1],
              a.m128_f32[2], a.m128_f32[3] );
}
```

```Output
54.000000 0.000000 0.000000 0.000000
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[__m128](../cpp/m128.md)<br/>
[Intrinsische Compilerfunktionen](../intrinsics/compiler-intrinsics.md)