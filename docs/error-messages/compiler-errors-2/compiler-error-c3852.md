---
title: Compilerfehler C3852
ms.date: 11/04/2016
f1_keywords:
- C3852
helpviewer_keywords:
- C3852
ms.assetid: 194e5c5e-0dfb-414e-86db-791c11eb610c
ms.openlocfilehash: 4ad7718f4efbeb3b0bc481755fd239615ab796cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380928"
---
# <a name="compiler-error-c3852"></a>Compilerfehler C3852

'Member' mit Typ 'Typ': aggregatsinitialisierung konnte diesen Member nicht initialisieren

Es wurde versucht, standardmäßig initialisiert als Teil einer aggregierter Initialisierung einem Datenmember zuweisen, die in eine aggregatinitialisierung nicht standardmäßig initialisiert empfangen kann.

In den folgenden Beispielen C3852 generiert:

```
// C3852.cpp
struct S
{
   short s;
};

struct S1
{
   int i;
   const S s;
};

struct S2
{
   int i;
   char & rc;
};

int main()
{
   S1 s1 = { 1 };   // C3852 const member
   // try the following line instead
   // S1 s1 = { 1, 2 };

   S2 s2 = { 2 };   // C3852 reference member
   // try the following line instead
   // char c = 'a';
   S2 s2 = { 2, c };
}
```