---
title: Compilerfehler C3141
ms.date: 11/04/2016
f1_keywords:
- C3141
helpviewer_keywords:
- C3141
ms.assetid: b4fd65c3-50cc-46cd-8de0-6a6d24cb9cda
ms.openlocfilehash: e19de95b5b2c967d71a4b06aca431df8ffe9dc14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374936"
---
# <a name="compiler-error-c3141"></a>Compilerfehler C3141

"Schnittstellenname": Schnittstellen unterstützen nur öffentliche Vererbung

Schnittstellen, die definiert, mit der [-Schnittstelle (oder __interface)](../../cpp/interface.md) Schlüsselwort nur öffentliche Vererbung unterstützt.

Im folgende Beispiel wird die C3141 generiert:

```
// C3141.cpp
__interface IBase {};
__interface IDerived1 : protected IBase {};  // C3141
__interface IDerived2 : private IBase {};    // C3141
```