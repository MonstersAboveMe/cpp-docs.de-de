---
title: Ziele in mehreren Beschreibungsblöcken
ms.date: 11/04/2016
helpviewer_keywords:
- description blocks
- blocks, multiple description
- multiple description blocks
ms.assetid: 8618dcd9-c11d-4562-91a7-0c904ed438a8
ms.openlocfilehash: 03a6e1d0be44e12bb76767b7334ab647a6054b6e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317379"
---
# <a name="targets-in-multiple-description-blocks"></a>Ziele in mehreren Beschreibungsblöcken

Geben Sie zwei aufeinander folgende Doppelpunkte (:) zwischen den Zielen und abhängigen Dateien, um ein Ziel in mehreren Beschreibungsblöcken mit verschiedenen Befehlen zu aktualisieren.

```
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

## <a name="see-also"></a>Siehe auch

[Ziele](targets.md)
