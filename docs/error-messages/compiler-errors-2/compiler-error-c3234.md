---
title: Compilerfehler C3234
ms.date: 11/04/2016
f1_keywords:
- C3234
helpviewer_keywords:
- C3234
ms.assetid: ebefc15a-e40d-424b-a3dd-d7e185d0ed7b
ms.openlocfilehash: fd6e918c115ed121dda5d589a62b1a94d14184a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175256"
---
# <a name="compiler-error-c3234"></a>Compilerfehler C3234

Eine generische Klasse kann nicht von einem generischen Typparameter abgeleitet werden.

Eine generische Klasse kann nicht von einem generischen Typparameter erben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3234 generiert:

```
// C3234.cpp
// compile with: /clr /c
generic <class T>
public ref class C : T {};   // C3234
// try the following line instead
// public ref class C {};
```