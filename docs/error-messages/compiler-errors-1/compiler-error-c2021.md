---
title: Compilerfehler C2021
ms.date: 11/04/2016
f1_keywords:
- C2021
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
ms.openlocfilehash: 6492dfffbb5a2f80ea543d4248c0f77759c0a521
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303601"
---
# <a name="compiler-error-c2021"></a>Compilerfehler C2021

Exponentwert erwartet und nicht „character“.

Das Zeichen als Exponent einer Gleitkommakonstanten verwendet ist keine gültige Zahl. Achten Sie darauf, dass Sie einen Exponenten zu verwenden, der im Bereich befindet.

## <a name="example"></a>Beispiel

Im folgende Beispiel wird die C2021 generiert:

```
// C2021.cpp
float test1=1.175494351E;   // C2021
```

## <a name="example"></a>Beispiel

Mögliche Lösung:

```
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```