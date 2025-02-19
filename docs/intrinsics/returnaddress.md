---
title: _ReturnAddress
ms.date: 11/04/2016
f1_keywords:
- _ReturnAddress
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
ms.openlocfilehash: e5013b20f9e7ed0349d940d9be61cc1b4afc95d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390450"
---
# <a name="returnaddress"></a>_ReturnAddress

## <a name="microsoft-specific"></a>Microsoft-spezifisch

Die `_ReturnAddress` systeminterne enthält die Adresse der Anweisung in der aufrufenden Funktion, die ausgeführt wird, nachdem die Steuerung an den Aufrufer zurückgibt.

Erstellen Sie das folgende Programm und die schrittweise durchlaufen im Debugger. Beachten Sie die Adresse, die von zurückgegeben wird, wie Sie das Programm durchgehen schrittweise, `_ReturnAddress`. Klicken Sie dann sofort nach der Rückgabe der Funktion, in denen `_ReturnAddress` wurde verwendet wird, öffnen die [Vorgehensweise: Verwenden des Disassembierungsfensters](/visualstudio/debugger/how-to-use-the-disassembly-window) und notieren Sie sich, dass die Adresse, der die nächste Anweisung ausgeführt werden, die Adresse, die von zurückgegeben entspricht `_ReturnAddress`.

Optimierungen wie z. B. inlining Mai Auswirkungen auf die Rückgabeadresse. Angenommen, das unten angegebene Beispielprogramm kompiliert wird, mit [/Ob1](../build/reference/ob-inline-function-expansion.md), `inline_func` werden in der aufrufenden Funktion inline `main`. Aus diesem Grund die Aufrufe an `_ReturnAddress` aus `inline_func` und `main` wird jeweils den gleichen Wert zu erzeugen.

Wenn `_ReturnAddress` wird verwendet, in einem Programm mit kompiliert ["/ CLR"](../build/reference/clr-common-language-runtime-compilation.md), die Funktion mit der `_ReturnAddress` Aufruf wird als eine native Funktion kompiliert werden. Wenn eine Funktion als kompiliert verwaltete Aufrufe an die Funktion mit `_ReturnAddress`, `_ReturnAddress` Verhalten sich womöglich nicht wie erwartet.

## <a name="requirements"></a>Anforderungen

**Headerdatei** \<intrin.h >

## <a name="example"></a>Beispiel

```
// compiler_intrinsics__ReturnAddress.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_ReturnAddress)

__declspec(noinline)
void noinline_func(void)
{
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());
}

__forceinline
void inline_func(void)
{
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());
}

int main(void)
{
   noinline_func();
   inline_func();
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());

   return 0;
}
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)<br/>
[Intrinsische Compilerfunktionen](../intrinsics/compiler-intrinsics.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)