---
title: Compilerfehler C3345
ms.date: 11/04/2016
f1_keywords:
- C3345
helpviewer_keywords:
- C3345
ms.assetid: 1dda4c79-73bb-441b-b939-746154c3afba
ms.openlocfilehash: eb1d15a12bfebbf44f7335a848d68c367c285586
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300595"
---
# <a name="compiler-error-c3345"></a>Compilerfehler C3345

'identifizierer': Unzulässiger Bezeichner für den Modulnamen

Der *Bezeichner* für ein Modul enthält mindestens ein ungültiges Zeichen. Ein Bezeichner ist gültig, wenn das erste Zeichen ein Buchstabe, ein Unterstrich oder ein hohes ANSI-Zeichen (0x80-FF) und jedes nachfolgende Zeichen alphanumerisch, ein Unterstrich oder ein hohes ANSI-Zeichen ist.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Stellen Sie sicher, dass der *Bezeichner* keine Leerzeichen oder sonstigen ungültigen Zeichen enthält.

## <a name="example"></a>Beispiel

Das folgende Codebeispiel verursacht Fehlermeldung C3345, da der `name` -Parameter des `module` -Attributs ein Leerzeichen enthält.

```
// cpp_attr_name_module.cpp
// compile with: /LD /link /OPT:NOREF
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

// C3345 expected
[module(dll, name="My Library", version="1.2", helpfile="MyHelpFile")]
// Try the following line instead
//[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]
// Module attribute now applies to this class
class CMyClass {
public:
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {
   // add your own code here
   return __super::DllMain(dwReason, lpReserved);
   }
};
```

## <a name="see-also"></a>Siehe auch

[__iscsym](../../c-runtime-library/reference/iscsym-functions.md)<br/>
[Zeichenklassifizierung](../../c-runtime-library/character-classification.md)<br/>
[module](../../windows/module-cpp.md)