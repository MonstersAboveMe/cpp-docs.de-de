---
title: Drag &amp; Drop-Operationen für das Struktursteuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
ms.openlocfilehash: c7febeec513d8004df2bd1cc42e4e97e027e9f17
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167698"
---
# <a name="tree-control-drag-and-drop-operations"></a>Drag &amp; Drop-Operationen für das Struktursteuerelement

Ein Strukturansicht-Steuerelement ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) sendet eine Benachrichtigung, wenn der Benutzer beginnt, ein Element zu ziehen. Das Steuerelement sendet eine [TVN_BEGINDRAG](/windows/desktop/Controls/tvn-begindrag) Benachrichtigung, wenn der Benutzer beginnt, ziehen ein Element mit die linke Maustaste gedrückt und [TVN_BEGINRDRAG](/windows/desktop/Controls/tvn-beginrdrag) Benachrichtigung, wenn der Benutzer beginnt, ziehen die Rechte Taste. Sie können verhindern, dass ein Strukturansicht-Steuerelement diese Benachrichtigungen senden, ermöglicht der Strukturansicht den TVS_DISABLEDRAGDROP-Stil.

Sie erhalten ein Bild anzuzeigenden während eines Ziehvorgangs durch Aufrufen der [Memberfunktion CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) Member-Funktion. Das Strukturansicht-Steuerelement erstellt, eine ziehen Bitmap, die basierend auf der Bezeichnung des Elements, das gezogen wird. Das Strukturansicht-Steuerelement erstellt eine Bildliste an, die Bitmap hinzugefügt, und gibt einen Zeiger auf die [CImageList](../mfc/reference/cimagelist-class.md) Objekt.

Sie müssen den Code bereitstellen, der tatsächlich das Element gezogen wird. Dies umfasst in der Regel mithilfe der ziehen Funktionen von der Liste Bildfunktionen und Verarbeiten der [WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove) und [WM_LBUTTONUP](/windows/desktop/inputdev/wm-lbuttonup) (oder [WM_RBUTTONUP](/windows/desktop/inputdev/wm-rbuttonup)) die Nachrichten gesendet, nachdem der Ziehvorgang begonnen wurde. Weitere Informationen zu den Funktionen der Image-Liste finden Sie unter [CImageList](../mfc/reference/cimagelist-class.md) in die *MFC-Referenz* und [Bilderlisten](/windows/desktop/controls/image-lists) im Windows SDK. Weitere Informationen zum Verschieben einer Strukturelement-Steuerelement, finden Sie unter [ziehen das Strukturansichtselement](/windows/desktop/Controls/tree-view-controls), auch im Windows SDK.

Wenn Elemente in einem Strukturansicht-Steuerelement die Ziele eines Drag & Drop-Vorgangs werden sollen, müssen Sie wissen, wenn der Mauszeiger auf ein Zielelement ist. Sie erhalten durch Aufrufen der [HitTest](../mfc/reference/ctreectrl-class.md#hittest) Member-Funktion. Sie geben Sie einen Punkt und ganze Zahl oder die Adresse einer [TVHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvhittestinfo) Struktur, die die aktuellen Koordinaten des Mauszeigers enthält. Wenn die Funktion zurückgibt, enthält die ganze Zahl oder eine Struktur ein Flag, das die Position des Mauszeigers in Bezug auf die Strukturansicht-Steuerelement. Wenn der Cursor über ein Element in der Strukturansicht-Steuerelement ist, enthält die Struktur das Handle für das Element auch.

Sie können angeben, dass ein Element das Ziel eines Drag & Drop-Vorgangs durch Aufrufen der [SetItem](../mfc/reference/ctreectrl-class.md#setitem) Member-Funktion zum Festlegen des Status, um die `TVIS_DROPHILITED` Wert. Ein Element mit diesem Status wird in den Stil an, dass ein Drag & Drop-Ziel gezeichnet wird.

## <a name="see-also"></a>Siehe auch

[Verwenden von CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
