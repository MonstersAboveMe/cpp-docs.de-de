---
title: Compilerfehler C2707
ms.date: 11/04/2016
f1_keywords:
- C2707
helpviewer_keywords:
- C2707
ms.assetid: 3deaf45c-74da-4c9d-acc6-b82412720b74
ms.openlocfilehash: ce86f69b36b915b3e757b5d18430c99cb288e4e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161003"
---
# <a name="compiler-error-c2707"></a>Compilerfehler C2707

'Bezeichner': Falscher Kontext für systeminterne Funktion

Strukturierte Ausnahmebehandlung systeminternen Funktionen sind in bestimmten Kontexten ungültig:

- `_exception_code()` außerhalb eines Ausnahmefilters oder `__except` blockieren

- `_exception_info()` außerhalb eines Ausnahmefilters

- `_abnormal_termination()` außerhalb einer `__finally` blockieren

Um den Fehler zu beheben, achten Sie darauf, dass die Ausnahmebehandlung systeminternen Funktionen im geeigneten Kontext platziert werden.

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C2707 generiert.

```
// C2707.cpp
#include <windows.h>
#include <stdio.h>

LONG MyFilter(LONG excode)
{
    return (excode == EXCEPTION_ACCESS_VIOLATION ?
        EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);   // OK
}

LONG func(void)
{
    int x, y;
    return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ?  // C2707
             EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);

    __try
    {
        y = 0;
        x = 4 / y;
        return 0;
     }

    __except(MyFilter(GetExceptionCode()))
    {
        return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ? // ok
               EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);
    }
}

int main()
{
    __try
    {
        func();
    } __except(EXCEPTION_EXECUTE_HANDLER)
    {
        printf_s("Caught exception\n");
    }
}
```