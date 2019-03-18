---
title: Mehrere Ziele
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
ms.openlocfilehash: 43e5216d5e11e89aff9b6f0c69ff4e76a8cc9da8
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825288"
---
# <a name="multiple-targets"></a>Mehrere Ziele

NMAKE wertet mehrere Ziele in einer einzigen Abhängigkeit, als ob jeder in einem separaten Beschreibungsblock angegeben wurden.

Dies z. B....

```Output
bounce.exe leap.exe : jump.obj
   echo Building...
```

.. Auswertung:

```Output
bounce.exe : jump.obj
   echo Building...
leap.exe : jump.obj
   echo Building...
```

## <a name="see-also"></a>Siehe auch

[Ziele](targets.md)