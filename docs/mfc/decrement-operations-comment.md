---
title: --Operations-Kommentar
ms.date: 11/04/2016
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
ms.openlocfilehash: 7e4d0549d3d77916df532f105dc58ed9e9f78af2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240599"
---
# <a name="-operations-comment"></a>// Operations-Kommentar

Die `// Operations` Abschnitt der Deklaration einer MFC-Klasse enthält Member-Funktionen, die Sie, auf das Objekt aufrufen können, das können sie die Schritte oder Aktionen, die (Vorgänge). Diese Funktionen sind in der Regel nicht -**const** , da sie in der Regel Nebeneffekte haben. Sie können virtuell oder je nach den Anforderungen der Klasse nicht virtuell sein. In der Regel sind diese Member öffentlich.

In diesem Beispiel aus der Klasse auflisten `CStdioFile`im [ein Beispiel für die Kommentare](../mfc/an-example-of-the-comments.md), die Liste enthält zwei Memberfunktionen unter diesen Kommentar: `ReadString` und `WriteString`.

Wie bei Attributen, können Vorgängen weiter unterteilt werden.

## <a name="see-also"></a>Siehe auch

[Verwenden der MFC-Quelldateien](../mfc/using-the-mfc-source-files.md)<br/>
[Ein Beispiel für die Kommentare](../mfc/an-example-of-the-comments.md)<br/>
[/ / Implementierungskommentar](../mfc/decrement-implementation-comment.md)<br/>
[/ Constructors-Kommentar](../mfc/decrement-constructors-comment.md)<br/>
[Attributekommentar](../mfc/decrement-attributes-comment.md)<br/>
[/ / Overridables-Kommentar](../mfc/decrement-overridables-comment.md)
