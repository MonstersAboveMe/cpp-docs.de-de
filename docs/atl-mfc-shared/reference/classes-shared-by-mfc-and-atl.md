---
title: Von MFC und ATL freigegebenen Klassen
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: 5376a87aac2b82615cd48f80e0e95208b8132bf0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235145"
---
# <a name="classes-shared-by-mfc-and-atl"></a>Von MFC und ATL freigegebenen Klassen

Die folgende Tabelle enthält die von MFC und ATL freigegebenen Klassen

|Klasse|Beschreibung|Header-Datei|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|Stellt Methoden für die Verwaltung von einer Datei zugeordneten Werte für Datum und Uhrzeit.|atltime.h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|Stellt Methoden für die Verwaltung von relative Datum- und Zeitwerte, die einer Datei zugeordnet.|atltime.h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|Stellt ein Zeichenfolgenobjekt mit einem festen Zeichenpuffer dar.|cstringt.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Bietet erweiterte Bitmapunterstützung, einschließlich der Möglichkeit zum Laden und Speichern von Bildern in JPEG, GIF, BMP und Portable Network Graphics (PNG).|atlimage.h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|Kapselt die DATE-Datentyp in OLE-Automatisierung verwendet.|atlcomtime.h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|Stellt einen relativen Zeitpunkt, eine Zeitspanne dar.|atlcomtime.h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|Eine Klasse, die ähnlich wie die Windows [Punkt](/windows/desktop/api/windef/ns-windef-tagpoint) -Struktur, die Member-Funktionen zum Bearbeiten von der ereignissteuerung `CPoint` und `POINT` Strukturen.|atltypes.h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|Eine Klasse, die ähnlich wie eine Windows [RECT](/windows/desktop/api/windef/ns-windef-tagrect) -Struktur, die Member-Funktionen zum Bearbeiten von der ereignissteuerung `CRect` Objekte und Windows `RECT` Strukturen.|atltypes.h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|Stellt eine `CSimpleStringT` Objekt.|atlsimpstr.h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|Eine Klasse, die ähnlich wie die Windows [Größe](/windows/desktop/api/windef/ns-windef-tagsize) -Struktur, die eine relative Koordinate oder Position implementiert.|atltypes.h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|Bietet automatische ressourcenbereinigung für `GetBuffer` und `ReleaseBuffer` Ruft für eine vorhandene `CStringT` Objekt.|atlsimpstr.h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|Stellt die Daten von einem String-Objekt.|atlsimpstr.h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|Stellt eine `CStringT` Objekt.|CStringT.h (MFC-abhängig) atlstr.h (MFC-unabhängig)|
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|Stellt eine absolute Zeit und Datum dar.|atltime.h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|Eine Zeitspanne, die intern als die Anzahl der Sekunden, in dem Zeitraum gespeichert ist.|atltime.h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|Stellt die Schnittstelle zu einem `CStringT` Speicher-Manager.|atlsimpstr.h|

## <a name="see-also"></a>Siehe auch

[Freigegebene ATL-/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
