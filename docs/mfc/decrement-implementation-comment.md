---
title: --Implementierungskommentar
ms.date: 11/04/2016
helpviewer_keywords:
- Implementation comment in MFC source files
- comments, MFC
- MFC source files, Implementation comment
- comments, Implementation comments
ms.assetid: 4d799c07-8e71-4a6b-90ab-8282d6ff48ce
ms.openlocfilehash: 377997b66c5b9c005d1e1bee24890b756621b672
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240736"
---
# <a name="-implementation-comment"></a>// Implementierungskommentar

Die `// Implementation` Abschnitt ist der wichtigste Teil einer Deklaration MFC-Klasse.

Dieser Abschnitt enthält alle Details zur Implementierung. Sowohl der Membervariablen als auch der Member-Funktionen können in diesem Abschnitt werden angezeigt. Alle Elemente in dieser Zeile konnte in einer zukünftigen Version von MFC geändert werden. Es sei denn, Sie es nicht vermeiden lassen, Sie dürfen nicht abhängig sein Details finden Sie unten die `// Implementation` Zeile. Unterhalb der Linie Implementierung deklarierten Member sind darüber hinaus nicht dokumentiert, zwar eine gewisse Implementierung in technische Hinweise erläutert wird. Überschreibungen virtueller Funktionen in der Basisklasse befinden sich in diesem Abschnitt, unabhängig davon, welcher Abschnitt Funktion der Basisklasse, definiert ist, da die Tatsache, dass eine Funktion Implementierung der Basisklasse überschreibt, ein Implementierungsdetail ist. In der Regel diese Elemente sind geschützt, aber nicht immer.

Beachten Sie, dass von der `CStdioFile` unter auflisten [ein Beispiel für die Kommentare](../mfc/an-example-of-the-comments.md) , dass die folgenden Member deklariert die `// Implementation` Kommentar kann deklariert werden, als **öffentliche**, **geschützt**, oder **private**. Sie sollten mit Vorsicht, nur diese Member verwenden, da sie in der Zukunft ändern können. Deklarieren eine Gruppe von Elementen als **öffentliche** müssen ggf. für die Implementierung der Klassenbibliothek ordnungsgemäß funktioniert. Dies bedeutet jedoch nicht, dass Sie problemlos so deklarierten Member verwenden können.

> [!NOTE]
>  Kommentare zu den übrigen Typen, die oberhalb oder unterhalb der `// Implementation` Kommentar. In beiden Fällen beschreiben sie die Arten von Membern unter ihnen deklariert werden. Wenn sie die folgenden auftreten der `// Implementation` kommentieren, Sie sollten davon ausgehen, dass die Elemente in künftigen Produktversionen von MFC ändern können.

## <a name="see-also"></a>Siehe auch

[Verwenden der MFC-Quelldateien](../mfc/using-the-mfc-source-files.md)<br/>
[Ein Beispiel für die Kommentare](../mfc/an-example-of-the-comments.md)<br/>
[/ Constructors-Kommentar](../mfc/decrement-constructors-comment.md)<br/>
[Attributekommentar](../mfc/decrement-attributes-comment.md)<br/>
[Vorgänge-Kommentar](../mfc/decrement-operations-comment.md)<br/>
[/ / Overridables-Kommentar](../mfc/decrement-overridables-comment.md)
