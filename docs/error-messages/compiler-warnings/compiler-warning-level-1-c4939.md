---
title: Compilerwarnung (Stufe 1) C4939
ms.date: 11/04/2016
f1_keywords:
- C4939
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
ms.openlocfilehash: 00526b3dae5035fe96ec1abb50bbdd056ceecfaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408250"
---
# <a name="compiler-warning-level-1-c4939"></a>Compilerwarnung (Stufe 1) C4939

\#Pragma-Vtordisp ist veraltet und wird in einer zukünftigen Version von Visual C++ entfernt

Das [vtordisp](../../preprocessor/vtordisp.md) -Pragma wird in einer der nächsten Versionen von Visual C++ entfernt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4939 generiert.

```
// C4939.cpp
// compile with: /c /W1
#pragma vtordisp(off)   // C4939
```