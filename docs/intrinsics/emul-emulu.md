---
title: __emul, __emulu
ms.date: 11/04/2016
f1_keywords:
- __emulu_cpp
- __emul
- __emul_cpp
- __emulu
helpviewer_keywords:
- __emul intrinsic
- __emulu intrinsic
ms.assetid: 79545236-cca2-40b8-a4e1-8abce9b26311
ms.openlocfilehash: 8657c0fb034ac6bbcfbebb946e059ad08d9e7046
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62264048"
---
# <a name="emul-emulu"></a>__emul, __emulu

**Microsoft-spezifisch**

Führt Multiplikationen, die überlaufen, was eine 32-Bit-Ganzzahl aufnehmen kann.

## <a name="syntax"></a>Syntax

```
__int64 __emul(
   int a,
   int b
);
unsigned __int64 __emulu(
   unsigned int a,
   unsigned int b
);
```

#### <a name="parameters"></a>Parameter

*a*<br/>
[in] Der erste Operand vom Typ ganze Zahl der Multiplikation.

*b*<br/>
[in] Der zweite Operand vom Typ ganze Zahl der Multiplikation.

## <a name="return-value"></a>Rückgabewert

Das Ergebnis der Multiplikation.

## <a name="requirements"></a>Anforderungen

|Systemintern|Architektur|
|---------------|------------------|
|`__emul`|x86, x64|
|`__emulu`|x86, x64|

**Headerdatei** \<intrin.h >

## <a name="remarks"></a>Hinweise

`__emul` akzeptiert zwei 32-Bit-Werte mit Vorzeichen und gibt das Ergebnis der Multiplikation als ein 64-Bit-Ganzzahlwert mit Vorzeichen zurück.

`__emulu` akzeptiert zwei 32-Bit-Ganzzahlwerte ohne Vorzeichen und gibt das Ergebnis der Multiplikation als ein 64-Bit-Ganzzahlwert ohne Vorzeichen zurück.

## <a name="example"></a>Beispiel

```
// emul.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__emul)
#pragma intrinsic(__emulu)

int main()
{
   int a = -268435456;
   int b = 2;

   __int64 result = __emul(a, b);

   cout << a << " * " << b << " = " << result << endl;

   unsigned int ua = 0xFFFFFFFF; // Dec value: 4294967295
   unsigned int ub = 0xF000000;  // Dec value: 251658240

   unsigned __int64 uresult = __emulu(ua, ub);

   cout << ua << " * " << ub << " = " << uresult << endl;

}
```

## <a name="output"></a>Output

```
-268435456 * 2 = -536870912
4294967295 * 251658240 = 1080863910317260800
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Intrinsische Compilerfunktionen](../intrinsics/compiler-intrinsics.md)