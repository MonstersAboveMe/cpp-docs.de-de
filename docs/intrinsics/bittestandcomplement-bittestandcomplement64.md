---
title: _bittestandcomplement, _bittestandcomplement64
ms.date: 11/04/2016
f1_keywords:
- _bittestandcomplement64
- _bittestandcomplement64_cpp
- _bittestandcomplement_cpp
- _bittestandcomplement
helpviewer_keywords:
- btc instruction
- _bittestandcomplement intrinsic
- _bittestandcomplement64 intrinsic
ms.assetid: 53fa12dd-835e-4e5d-baec-a431c8678806
ms.openlocfilehash: 4c0fc11ca890c64da3ff41c8679a17a733c81d4c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62264237"
---
# <a name="bittestandcomplement-bittestandcomplement64"></a>_bittestandcomplement, _bittestandcomplement64

**Microsoft-spezifisch**

Erzeugen Sie eine Anweisung, die Bit `b` der Adresse `a` untersucht, den aktuellen Wert zurückgibt und das Bit auf seiner Ergänzung setzt.

## <a name="syntax"></a>Syntax

```
unsigned char _bittestandcomplement(
   long *a,
   long b
);
unsigned char _bittestandcomplement64(
   __int64 *a,
   __int64 b
);
```

#### <a name="parameters"></a>Parameter

*a*<br/>
[in, out] Ein Zeiger auf den zu untersuchenden Speicher.

*b*<br/>
[in] Die zu testende Bitposition.

## <a name="return-value"></a>Rückgabewert

Das Bit an der angegebenen Position.

## <a name="requirements"></a>Anforderungen

|Systemintern|Architektur|
|---------------|------------------|
|`_bittestandcomplement`|x86, ARM, x64|
|`_bittestandcomplement64`|x64|

**Headerdatei** \<intrin.h >

## <a name="remarks"></a>Hinweise

Diese Routine ist nur als systeminterne Funktion verfügbar.

## <a name="example"></a>Beispiel

```
// bittestandcomplement.cpp
// processor: x86, IPF, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_bittestandcomplement)
#ifdef _M_AMD64
#pragma intrinsic(_bittestandcomplement64)
#endif

int main()
{
   long i = 1;
   __int64 i64 = 0x1I64;
   unsigned char result;
   printf("Initial value: %d\n", i);
   printf("Testing bit 1\n");
   result = _bittestandcomplement(&i, 1);
   printf("Value changed to %d, Result: %d\n", i, result);
#ifdef _M_AMD64
   printf("Testing bit 0\n");
   result = _bittestandcomplement64(&i64, 0);
   printf("Value changed to %I64d, Result: %d\n", i64, result);
#endif
}
```

## <a name="sample-output"></a>Beispielausgabe

```
Initial value: 1
Testing bit 1
Value changed to 3, Result: 0
Testing bit 0
Value changed to 0, Result: 1
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Intrinsische Compilerfunktionen](../intrinsics/compiler-intrinsics.md)