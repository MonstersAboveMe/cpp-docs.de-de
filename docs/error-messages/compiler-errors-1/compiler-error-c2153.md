---
title: Compilerfehler C2153
ms.date: 11/04/2016
f1_keywords:
- C2153
helpviewer_keywords:
- C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
ms.openlocfilehash: eeb7da509ffb1b8c408763c79d471586eb94f383
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175159"
---
# <a name="compiler-error-c2153"></a>Compilerfehler C2153

hexadezimale Konstanten müssen mindestens eine hexadezimale Ziffer enthalten.

Hexadezimale Konstanten 0 x 0 X und \x sind nicht gültig. Muss mindestens eine hexadezimale Ziffer folgen x oder X.

Im folgende Beispiel wird die C2153 generiert:

```
// C2153.cpp
int main() {
   int a= 0x;    // C2153
   int b= 0xA;   // OK
}
```