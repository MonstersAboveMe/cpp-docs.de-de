---
title: Zuweisungskonvertierungen
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
ms.openlocfilehash: 6caed3d7a8079bc6b02e9ad17859cd4062cbee7f
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152715"
---
# <a name="assignment-conversions"></a>Zuweisungskonvertierungen

Bei Zuweisungsvorgängen wird der Typ des zugewiesenen Werts in den Typ der Variablen konvertiert, die die Zuweisung empfängt. C lässt Konvertierungen durch Zuweisung zwischen Ganzzahl- und Gleitkommatypen zu, auch wenn Informationen in der Konvertierung verloren gehen. Die verwendete Konvertierungsmethode hängt von den Typen ab, die an der Zuweisung beteiligt sind, wie unter [Übliche arithmetische Konvertierungen](../c-language/usual-arithmetic-conversions.md) und in den folgenden Abschnitten beschrieben:

- [Konvertierungen von ganzzahligen Typen mit Vorzeichen](../c-language/conversions-from-signed-integral-types.md)

- [Konvertierungen von ganzzahligen Typen ohne Vorzeichen](../c-language/conversions-from-unsigned-integral-types.md)

- [Konvertierungen von Gleitkommatypen](../c-language/conversions-from-floating-point-types.md)

- [Konvertierungen in und aus Zeigertypen](../c-language/conversions-to-and-from-pointer-types.md)

- [Konvertierungen von anderen Typen](../c-language/conversions-from-other-types.md)

Typqualifizierer wirken sich nicht auf die Zulässigkeit der Konvertierung aus, obwohl der I-Wert **const** nicht auf der linken Seite der Zuweisung verwendet werden kann.

## <a name="see-also"></a>Siehe auch

[Typkonvertierungen](../c-language/type-conversions-c.md)
