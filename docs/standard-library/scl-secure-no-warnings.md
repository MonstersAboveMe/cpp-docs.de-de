---
title: _SCL_SECURE_NO_WARNINGS
ms.date: 11/04/2016
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
ms.openlocfilehash: 77c60aed511fc3dbbea2d74e83e36dae735dcb0e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348307"
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

Aufruf einer der potenziell unsicheren Methoden in der C++-Standardbibliothek führt zu [Compilerwarnung (Stufe 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Um diese Warnung zu deaktivieren, definieren Sie das Makro _SCL_SECURE_NO_WARNINGS in Ihrem Code ein:

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

Bei Verwendung vorkompilierter Header fügen Sie diese Richtlinie in der vorkompilierten Headerdatei ein, bevor Sie alle C-Laufzeitbibliothek oder standard-Bibliothek-Header einfügen. Wenn Sie es in einer einzelnen Quellcodedatei, setzen bevor Sie die vorkompilierte Headerdatei einschließen, wird es vom Compiler ignoriert.

## <a name="remarks"></a>Hinweise

Weitere Methoden zum Deaktivieren der Warnung C4996 sind u.a.:

- Mithilfe der Compileroption [/D (Präprozessordefinitionen)](../build/reference/d-preprocessor-definitions.md):

   > CL /D_SCL_SECURE_NO_WARNINGS [andere Compileroptionen] myfile.cpp

- Mithilfe der Compileroption [/w](../build/reference/compiler-option-warning-level.md):

   > CL-/wd4996 [andere Compileroptionen] myfile.cpp

- Mithilfe der Anweisung [#pragma warning](../preprocessor/warning.md):

   ```cpp
   #pragma warning(disable:4996)
   ```

Sie können die Stufe der Warnung C4996 mit der Compileroption **/w\<l >\<n >** auch manuell ändern. Um beispielsweise die Warnung C4996 auf Stufe 4 festzulegen:

> CL-/w44996 [andere Compileroptionen] myfile.cpp

Weitere Informationen finden Sie unter [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Warnstufe)](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Siehe auch

[Sichere Bibliotheken: C++-Standardbibliothek](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
