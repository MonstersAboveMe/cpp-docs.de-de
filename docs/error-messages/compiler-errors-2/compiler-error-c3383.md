---
title: Compilerfehler C3383
ms.date: 11/04/2016
f1_keywords:
- C3383
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
ms.openlocfilehash: 38aea188eeac90cd23d9203a53b4e630be2f115b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367335"
---
# <a name="compiler-error-c3383"></a>Compilerfehler C3383

"operator new" wird mit /clr:safe nicht unterstützt.

Die Ausgabedatei einer **/clr:safe** -Kompilierung ist Datei, die überprüfbar typsicher ist; Zeiger werden nicht unterstützt.

Weitere Informationen finden Sie unter

- [/clr (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Häufig auftretende 64-Bit-Migrationsprobleme bei Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3383 generiert:

```
// C3383.cpp
// compile with: /clr:safe
int main() {
   char* pCharArray = new char[256];  // C3383
}
```