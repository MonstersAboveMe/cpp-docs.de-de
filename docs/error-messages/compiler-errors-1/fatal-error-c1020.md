---
title: Schwerwiegender Fehler C1020
ms.date: 11/04/2016
f1_keywords:
- C1020
helpviewer_keywords:
- C1020
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
ms.openlocfilehash: bdd7a6c87b0e00bd7bef174b8daf0e16cc488a5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383151"
---
# <a name="fatal-error-c1020"></a>Schwerwiegender Fehler C1020

Unerwartetes #endif

Die `#endif` -Direktive hat keine entsprechende `#if`-, `#ifdef`- oder `#ifndef` -Direktive. Stellen Sie sicher, dass jede `#endif` -Direktive über eine entsprechende Direktive verfügt.

Im folgenden Beispiel wird C1020 generiert:

```
// C1020.cpp
#endif     // C1020
```

Mögliche Lösung:

```
// C1020b.cpp
// compile with: /c
#if 1
#endif
```