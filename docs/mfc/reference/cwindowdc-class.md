---
title: CWindowDC-Klasse
ms.date: 11/04/2016
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
ms.openlocfilehash: 55a9ccfc496c95c9e7410cbd5645135ee555ff26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323384"
---
# <a name="cwindowdc-class"></a>CWindowDC-Klasse

Abgeleitet von `CDC`.

## <a name="syntax"></a>Syntax

```
class CWindowDC : public CDC
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|Erstellt ein `CWindowDC`-Objekt.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|Das HWND zu der das `CWindowDC` angefügt ist.|

## <a name="remarks"></a>Hinweise

Ruft die Windows-Funktion [GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc)zur Erstellungszeit und [ReleaseDC](/windows/desktop/api/winuser/nf-winuser-releasedc) zur zerstörungszeit. Dies bedeutet, dass eine `CWindowDC` -Objekt greift auf den ganzen Bildschirmbereich eine [CWnd](../../mfc/reference/cwnd-class.md) (sowohl Client als auch nicht-Bereiche).

Weitere Informationen zur Verwendung von `CWindowDC`, finden Sie unter [Gerätekontexte](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>Anforderungen

Header: afxwin.h

##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC

Erstellt eine `CWindowDC` -Objekt, das den ganzen Bildschirmbereich (sowohl Client als auch nicht-Client) greift auf die `CWnd` Objekt verweist *aufnehmen*.

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Das Fenster, dessen Client-Bereich, der das Gerätekontext Objekt zugegriffen wird.

### <a name="remarks"></a>Hinweise

Der Konstruktor ruft die Windows-Funktion [GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc).

Eine Ausnahme (vom Typ `CResourceException`) wird ausgelöst, wenn die Windows `GetWindowDC` -Aufruf fehl. Ein Gerätekontext möglicherweise nicht verfügbar, wenn es sich bei allen Kontexten verfügbare Gerät Windows bereits zugewiesen wurde. Ihre Anwendung Computerressourcen für die fünf allgemeinen Anzeige Kontexte zu jedem Zeitpunkt unter Windows verfügbar.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd

Das HWND des der `CWnd` Zeiger zum Konstruieren der `CWindowDC` Objekt.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Hinweise

`m_hWnd` ist eine geschützte Variable des Typs HWND.

### <a name="example"></a>Beispiel

  Siehe das Beispiel für [CWindowDC::CWindowDC](#cwindowdc).

## <a name="see-also"></a>Siehe auch

[CDC-Klasse](../../mfc/reference/cdc-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDC-Klasse](../../mfc/reference/cdc-class.md)
