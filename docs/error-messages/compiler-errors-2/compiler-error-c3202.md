---
title: Compilerfehler C3202
ms.date: 11/04/2016
f1_keywords:
- C3202
helpviewer_keywords:
- C3202
ms.assetid: 23528a0c-5493-4804-9789-cd3c38e49fb9
ms.openlocfilehash: 5a81da1ee67d897b7a38d9968f7715be7b5af3d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402748"
---
# <a name="compiler-error-c3202"></a>Compilerfehler C3202

'Argumentname': Ungültiges Standardargument für den Vorlagenparameter 'Parameter'. Klassenvorlage erwartet

Sie haben ein ungültiges Standardargument für einen Vorlagenparameter übergeben.

Im folgenden Beispiel wird C3202 generiert:

```
// C3202.cpp
template<typename T>
class X
{
};

class Z
{
};

template<template<typename U> class T1 = Z, typename T2> // C3202
class Y
{
};
```