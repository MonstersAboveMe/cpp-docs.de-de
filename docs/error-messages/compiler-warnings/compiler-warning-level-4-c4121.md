---
title: Compilerwarnung (Stufe 4) C4121
ms.date: 11/04/2016
f1_keywords:
- C4121
helpviewer_keywords:
- C4121
ms.assetid: 8c5b85c9-2543-426b-88bc-319c50158c7e
ms.openlocfilehash: 0d02c5aff188a82062ae537f053157795d8925d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401370"
---
# <a name="compiler-warning-level-4-c4121"></a>Compilerwarnung (Stufe 4) C4121

'symbol': Ausrichtung eines Elements hängt vom Pragma 'pack' ab

Der Compiler hat eine Auffüllung hinzugefügt, um einen Strukturmember an der Ausrichtungsgrenze auszurichten, aber der Paketwert ist geringer als die Größe des Members. Beispielsweise wird durch folgenden Codeausschnitt C4121 erstellt:

```
// C4121.cpp
// compile with: /W4 /c
#pragma pack(2)
struct s
{
   char a;
   int b; // C4121
   long long c;
};
```

Nehmen Sie zur Behebung dieses Problems eine der folgenden Änderungen vor:

- Ändern Sie die Paketgröße mindestens auf die Größe des Members, der die Warnung verursacht hat. Ändern Sie beispielsweise in diesem Ausschnitt `pack(2)` in `pack(4)` oder `pack(8)`.

- Ordnen Sie die Memberdeklarationen aufsteigend nach Größe neu an. Kehren Sie im Codeausschnitt die Reihenfolge der Strukturmember um, sodass der Member `long long` vor `int` und der Member `int` vor `char` platziert ist.

Diese Warnung tritt nur auf, wenn der Compiler den Datenmembern eine Auffüllung voranstellt. Sie tritt nicht auf, wenn beim Packen Daten an einer Speicheradresse platziert werden, die für den Datentyp nicht ausgerichtet ist, aber dem Datenmember keine Auffüllung vorangestellt wurde. Daten, die nicht an Grenzen ausgerichtet sind, bei denen es sich um ein Vielfaches der Datengröße handelt, können die Leistung mindern. Lese- und Schreibvorgänge von nicht ausgerichteten Daten führen in manchen Architekturen zu Prozessorfehlern; die Behebung dieser Fehler nimmt zwei- bis dreimal mehr Zeit in Anspruch. Zugriffe auf nicht ausgerichtete Daten können zu einigen RISC-Architekturen nicht portiert werden.

Sie können [#pragma Pack](../../preprocessor/pack.md) oder [/Zp](../../build/reference/zp-struct-member-alignment.md) die strukturausrichtung an. (Wird nicht vom Compiler generiert diese Warnung, wenn **/Zp1** angegeben ist.)