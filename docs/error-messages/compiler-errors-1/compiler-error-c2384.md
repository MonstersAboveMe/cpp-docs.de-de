---
title: Compilerfehler C2384
ms.date: 11/04/2016
f1_keywords:
- C2384
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
ms.openlocfilehash: 1909fb999dd0f60224029b726f773c11fa69ee40
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347154"
---
# <a name="compiler-error-c2384"></a>Compilerfehler C2384

„Member“ : __declspec(thread) kann nicht auf einen Member einer managed- oder WinRT-Klasse angewendet werden.

Die [Thread](../../cpp/thread.md) `__declspec` Modifizierer kann nicht auf ein Member eines verwalteten oder Windows-Runtime-Klasse verwendet werden.

Statischer lokaler Threadspeicher kann im verwalteten Code nur für statisch geladene DLLs verwendet werden; die DLL muss bei Prozessstart statisch geladen sein. Windows-Runtime unterstützt keinen threadlokalen Speicher.

Mit der folgenden Zeile wird C2384 generiert und gezeigt, wie dieser Fehler im C++-/CLI-Code behoben werden kann:

```
// C2384.cpp
// compile with: /clr /c
public ref class B {
public:
   __declspec( thread ) static int tls_i = 1;   // C2384

   // OK - declare with attribute instead
   [System::ThreadStaticAttribute]
   static int tls_j;
};
```