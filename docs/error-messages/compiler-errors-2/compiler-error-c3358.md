---
title: Compilerfehler C3358
ms.date: 11/04/2016
f1_keywords:
- C3358
helpviewer_keywords:
- C3358
ms.assetid: 180b93df-e78f-441a-91fb-1594c681f7f0
ms.openlocfilehash: 8d57bf7447ba0c05585d3c18cfaaf960ddc0f968
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402618"
---
# <a name="compiler-error-c3358"></a>Compilerfehler C3358

"Symbol": Symbol konnte nicht gefunden werden

Das geforderte Symbol wurde nicht gefunden.

Im folgenden Beispiel wird C3358 generiert:

```
// C3358.cpp
#define __ATLEVENT_H__ 1   // remove this line to resolve the error
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[event_receiver(com)]
struct A   // C3358
{
   void func();
};

int main()
{
}
```