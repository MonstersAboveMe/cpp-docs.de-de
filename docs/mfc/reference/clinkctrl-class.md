---
title: CLinkCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CLinkCtrl
- AFXCMN/CLinkCtrl
- AFXCMN/CLinkCtrl::CLinkCtrl
- AFXCMN/CLinkCtrl::Create
- AFXCMN/CLinkCtrl::CreateEx
- AFXCMN/CLinkCtrl::GetIdealHeight
- AFXCMN/CLinkCtrl::GetIdealSize
- AFXCMN/CLinkCtrl::GetItem
- AFXCMN/CLinkCtrl::GetItemID
- AFXCMN/CLinkCtrl::GetItemState
- AFXCMN/CLinkCtrl::GetItemUrl
- AFXCMN/CLinkCtrl::HitTest
- AFXCMN/CLinkCtrl::SetItem
- AFXCMN/CLinkCtrl::SetItemID
- AFXCMN/CLinkCtrl::SetItemState
- AFXCMN/CLinkCtrl::SetItemUrl
helpviewer_keywords:
- CLinkCtrl [MFC], CLinkCtrl
- CLinkCtrl [MFC], Create
- CLinkCtrl [MFC], CreateEx
- CLinkCtrl [MFC], GetIdealHeight
- CLinkCtrl [MFC], GetIdealSize
- CLinkCtrl [MFC], GetItem
- CLinkCtrl [MFC], GetItemID
- CLinkCtrl [MFC], GetItemState
- CLinkCtrl [MFC], GetItemUrl
- CLinkCtrl [MFC], HitTest
- CLinkCtrl [MFC], SetItem
- CLinkCtrl [MFC], SetItemID
- CLinkCtrl [MFC], SetItemState
- CLinkCtrl [MFC], SetItemUrl
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
ms.openlocfilehash: 38f529f46623bc7095879b29fba09427626073ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62225479"
---
# <a name="clinkctrl-class"></a>CLinkCtrl-Klasse

Stellt die Funktionalität des allgemeinen Windows-SysLink-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CLinkCtrl::CLinkCtrl](#clinkctrl)|Erstellt ein `CLinkCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CLinkCtrl::Create](#create)|Erstellt ein Linksteuerelement, und fügt sie an einer `CLinkCtrl` Objekt.|
|[CLinkCtrl::CreateEx](#createex)|Erstellt ein Linksteuerelement mit erweiterten Stile und fügt sie an einer `CLinkCtrl` Objekt.|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Ruft die optimale Höhe des Linksteuerelements an.|
|[CLinkCtrl::GetIdealSize](#getidealsize)|Berechnet die bevorzugte Höhe der Text des Links für das aktuelle Linksteuerelement, abhängig von der angegebenen Breite des Links.|
|[CLinkCtrl::GetItem](#getitem)|Ruft ab, die Status und Attribute eines Elements der Link-Steuerelement.|
|[CLinkCtrl::GetItemID](#getitemid)|Ruft die ID des Elements eine Link-Steuerelement ab.|
|[CLinkCtrl::GetItemState](#getitemstate)|Ruft den Zustand des Elements die Link-Steuerelement ab.|
|[CLinkCtrl::GetItemUrl](#getitemurl)|Ruft die URL, die durch die Link-Steuerelement ein Element dargestellt wird.|
|[CLinkCtrl::HitTest](#hittest)|Bestimmt, ob der Benutzer den angegebenen Link geklickt hat.|
|[CLinkCtrl::SetItem](#setitem)|Legt fest, die Status und Attribute eines Elements der Link-Steuerelement.|
|[CLinkCtrl::SetItemID](#setitemid)|Legt die ID des Elements eine Link-Steuerelement fest.|
|[CLinkCtrl::SetItemState](#setitemstate)|Legt den Status der Link-Steuerelement ein Element fest.|
|[CLinkCtrl::SetItemUrl](#setitemurl)|Legt fest, die URL, die durch die Link-Steuerelement ein Element dargestellt wird.|

## <a name="remarks"></a>Hinweise

Eine "link Control" bietet eine bequeme Möglichkeit, Hypertextlinks in einem Fenster einzubetten. Das tatsächliche Steuerelement ist ein Fenster, das markierte Text gerendert und die entsprechende Anwendungen startet, wenn der Benutzer einen Link klickt. Mehrere Links werden in einem Steuerelement unterstützt und können durch einen nullbasierten Index zugegriffen werden.

Dieses Steuerelement (und somit die `CLinkCtrl` Klasse) ist nur für Programme unter Windows XP und höher verfügbar.

Weitere Informationen finden Sie unter [SysLink-Steuerelement](/windows/desktop/Controls/syslink-overview) im Windows SDK.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>Anforderungen

**Header:** afxcmn.h

##  <a name="clinkctrl"></a>  CLinkCtrl::CLinkCtrl

Erstellt ein `CLinkCtrl`-Objekt.

```
CLinkCtrl();
```

##  <a name="create"></a>  CLinkCtrl::Create

Erstellt ein Linksteuerelement, und fügt sie an einer `CLinkCtrl` Objekt.

```
virtual BOOL Create(
    LPCTSTR lpszLinkMarkup,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*lpszLinkMarkup*<br/>
Zeiger auf eine 0 (null) endende Zeichenfolge, die anzuzeigenden Text gekennzeichnet enthält. Weitere Informationen finden Sie im Abschnitt "Markup and Link Access" im Thema [Übersicht der SysLink-Steuerelemente](/windows/desktop/Controls/syslink-overview).

*dwStyle*<br/>
Gibt die Link-Steuerelement-Stil. Wenden Sie eine beliebige Kombination der Stile von Listensteuerelementen. Finden Sie unter [allgemeinen Stile von Listensteuerelementen](/windows/desktop/Controls/common-control-styles) in die `Windows SDK` für Weitere Informationen.

*rect*<br/>
Gibt an, den des Linksteuerelements Größe und Position. Es kann sein, entweder eine [CRect](../../atl-mfc-shared/reference/crect-class.md) Objekt oder ein [RECT](/windows/desktop/api/windef/ns-windef-tagrect) Struktur.

*pParentWnd*<br/>
Gibt an, die linksteuerung übergeordnete Fenster. Es darf nicht NULL sein.

*nID*<br/>
Gibt die Link-Steuerelement-ID an.

### <a name="return-value"></a>Rückgabewert

True, wenn die Initialisierung erfolgreich war. andernfalls "false".

### <a name="remarks"></a>Hinweise

Sie erstellen eine `CLinkCtrl` Objekt in zwei Schritten. Zunächst rufen Sie den Konstruktor, und rufen Sie anschließend `Create`, der die Link-Steuerelement erstellt, und fügt es der `CLinkCtrl` Objekt. Wenn Sie erweiterte Fensterstile mit dem Steuerelement verwenden möchten, rufen Sie [CLinkCtrl::CreateEx](#createex) anstelle von `Create`.

Die zweite Form der `Create` Methode ist veraltet. Verwenden Sie die erste Form, der angibt, die *LpszLinkMarkup* Parameter.

### <a name="example"></a>Beispiel

Das folgende Codebeispiel definiert zwei Variablen, die mit dem Namen `m_Link1` und `m_Link2`, mit denen die beiden Link-Steuerelemente zugreifen.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird ein Linksteuerelement basierend auf dem Standort eines anderen Steuerelements der Link erstellt. Das Ressourcenladeprogramm erstellt der erste Linksteuerelement beim Start der Anwendung. Wenn Ihre Anwendung die Methode OnInitDialog eingibt, erstellen Sie das zweite Linksteuerelement, relativ zur Position des ersten Linksteuerelements an. Klicken Sie dann ändern Sie den zweite Link-Steuerelement den Text angepasst, den es anzeigt.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

##  <a name="createex"></a>  CLinkCtrl::CreateEx

Erstellt ein Linksteuerelement mit erweiterten Stile und fügt sie an einer `CLinkCtrl` Objekt.

```
virtual BOOL CreateEx(
    LPCTSTR lpszLinkMarkup,
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL CreateEx(DWORD  dwExStyle,
    DWORD  dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT  nID);
```

### <a name="parameters"></a>Parameter

*lpszLinkMarkup*<br/>
Zeiger auf eine 0 (null) endende Zeichenfolge, die anzuzeigenden Text gekennzeichnet enthält. Weitere Informationen finden Sie im Abschnitt "Markup and Link Access" im Thema [Übersicht der SysLink-Steuerelemente](/windows/desktop/Controls/syslink-overview).

*dwExStyle*<br/>
Gibt den erweiterten Stil des Linksteuerelements an. Eine Liste der erweiterten Windows-Stile, finden Sie unter den *DwExStyle* -Parameter für [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) im Windows SDK.

*dwStyle*<br/>
Gibt die Link-Steuerelement-Stil. Wenden Sie eine beliebige Kombination der Stile von Listensteuerelementen. Weitere Informationen finden Sie unter [allgemeinen Stile von Listensteuerelementen](/windows/desktop/Controls/common-control-styles) im Windows SDK.

*rect*<br/>
Gibt an, den des Linksteuerelements Größe und Position. Es kann sein, entweder eine [CRect](../../atl-mfc-shared/reference/crect-class.md) Objekt oder ein [RECT](/windows/desktop/api/windef/ns-windef-tagrect) Struktur.

*pParentWnd*<br/>
Gibt an, die linksteuerung übergeordnete Fenster. Es darf nicht NULL sein.

*nID*<br/>
Gibt die Link-Steuerelement-ID an.

### <a name="return-value"></a>Rückgabewert

True, wenn die Initialisierung erfolgreich war. andernfalls "false".

### <a name="remarks"></a>Hinweise

Verwendung `CreateEx` anstelle von [erstellen](#create) erweiterte Konstanten der Windows-Stil angewendet.

Die zweite Form der `CreateEx` Methode ist veraltet. Verwenden Sie die erste Form, der angibt, die *LpszLinkMarkup* Parameter.

##  <a name="getidealheight"></a>  CLinkCtrl::GetIdealHeight

Ruft die optimale Höhe des Linksteuerelements an.

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>Rückgabewert

Die optimale Höhe des Steuerelements in Pixel.

### <a name="remarks"></a>Hinweise

Diese Memberfunktion implementiert das Verhalten der Win32-Nachricht [LM_GETIDEALHEIGHT](/windows/desktop/Controls/lm-getidealheight), wie im Windows SDK beschrieben.

##  <a name="getidealsize"></a>  CLinkCtrl::GetIdealSize

Berechnet die bevorzugte Höhe der Text des Links für das aktuelle Linksteuerelement, abhängig von der angegebenen Breite des Links.

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*cxMaxWidth*|[in] Die maximale Breite des Links in Pixeln.|
|[out] \* *pSize*|Ein Zeiger auf ein Windows [Größe](/windows/desktop/api/windef/ns-windef-tagsize) Struktur. Bei der Rückgabe dieser Methode die *cy* Mitglied der `SIZE` Struktur enthält die Höhe des idealen Link-Text für die Breite der Link-Text, der angegeben wird *CxMaxWidth*. Die *Cx* Member der Struktur enthält die Breite der Link-Text, der tatsächlich benötigt wird.|

### <a name="return-value"></a>Rückgabewert

Die bevorzugte Höhe der Text des Links in Pixeln. Der Rückgabewert ist identisch mit dem Wert, der die *cy* Mitglied der `SIZE` Struktur.

### <a name="remarks"></a>Hinweise

Ein Beispiel für die `GetIdealSize` -Methode, siehe das Beispiel in [CLinkCtrl::Create](#create).

Diese Methode sendet die [LM_GETIDEALSIZE](/windows/desktop/Controls/lm-getidealsize) -Nachricht, die im Windows SDK beschrieben wird.

##  <a name="getitem"></a>  CLinkCtrl::GetItem

Ruft ab, die Status und Attribute eines Elements der Link-Steuerelement.

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Ein Zeiger auf eine [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) -Struktur mit Informationen zu erhalten.

### <a name="return-value"></a>Rückgabewert

Gibt "true" bei Erfolg bei "false".

### <a name="remarks"></a>Hinweise

Diese Memberfunktion implementiert das Verhalten der Win32-Nachricht [LM_GETITEM](/windows/desktop/Controls/lm-getitem), wie im Windows SDK beschrieben.

##  <a name="getitemid"></a>  CLinkCtrl::GetItemID

Ruft die ID des Elements eine Link-Steuerelement ab.

```
BOOL GetItemID(
    int iLink,
    CString& strID) const;

BOOL GetItemID(
    int iLink,
    LPWSTR szID,
    UINT cchID) const;
```

### <a name="parameters"></a>Parameter

*iLink*<br/>
Der Index eines Elements der Link-Steuerelement.

*strID*<br/>
Ein [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) -Objekt, das die ID des angegebenen Elements enthält.

*szID*<br/>
Eine mit Null endende Zeichenfolge, die die ID des angegebenen Elements enthält.

*cchID*<br/>
Die Größe in Zeichen von der *SzID* Puffer.

### <a name="return-value"></a>Rückgabewert

Gibt "true" bei Erfolg bei "false".

> [!NOTE]
>  Diese Funktion gibt auch FALSE zurück, wenn der Puffer des *SzID oder StrID* MAX_LINKID_TEXT kleiner ist.

### <a name="remarks"></a>Hinweise

Ruft die ID des Elements einen bestimmten Link-Steuerelement ab. Weitere Informationen finden Sie auf die Win32-Meldung [LM_GETITEM](/windows/desktop/Controls/lm-getitem) im Windows SDK.

##  <a name="getitemstate"></a>  CLinkCtrl::GetItemState

Ruft den Zustand des Elements die Link-Steuerelement ab.

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>Parameter

*iLink*<br/>
Der Index eines Elements der Link-Steuerelement.

*pnState*<br/>
Der Wert des Elements angegebenen Zustand.

*stateMask*<br/>
Die Kombination von Flags, die der, der abzurufende Zustandselement beschreiben. Eine Liste von Werten, finden Sie unter der Beschreibung des der `state` Element in der [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) Struktur. Zulässigen Elemente sind identisch mit denen innerhalb von `state`.

### <a name="return-value"></a>Rückgabewert

Gibt "true" bei Erfolg bei "false".

### <a name="remarks"></a>Hinweise

Ruft den Wert des Elements angegebenen Status einen bestimmten Link-Steuerelement ein Element. Weitere Informationen finden Sie auf die Win32-Meldung [LM_GETITEM](/windows/desktop/Controls/lm-getitem) im Windows SDK.

##  <a name="getitemurl"></a>  CLinkCtrl::GetItemUrl

Ruft die URL, die durch die Link-Steuerelement ein Element dargestellt wird.

```
BOOL GetItemUrl(
    int iLink,
    CString& strUrl) const;

BOOL GetItemUrl(
    int iLink,
    LPWSTR szUrl,
    UINT cchUrl) const;
```

### <a name="parameters"></a>Parameter

*iLink*<br/>
Der Index eines Elements der Link-Steuerelement.

*strUrl*<br/>
Ein [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) Objekt mit der URL, die durch das angegebene Element dargestellt wird

*szUrl*<br/>
Eine Null-terminierte Zeichenfolge, die mit der URL, die durch das angegebene Element dargestellt wird

*cchUrl*<br/>
Die Größe in Zeichen von der *SzURL* Puffer.

### <a name="return-value"></a>Rückgabewert

Gibt "true" bei Erfolg bei "false".

> [!NOTE]
>  Diese Funktion gibt auch FALSE zurück, wenn der Puffer des *SzUrl oder StrUrl* MAX_LINKID_TEXT kleiner ist.

### <a name="remarks"></a>Hinweise

Ruft die URL, die durch den angegebenen Link-Steuerelement ein Element dargestellt wird. Weitere Informationen finden Sie auf die Win32-Meldung [LM_GETITEM](/windows/desktop/Controls/lm-getitem) im Windows SDK.

##  <a name="hittest"></a>  CLinkCtrl::HitTest

Bestimmt, ob der Benutzer den angegebenen Link geklickt hat.

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>Parameter

*phti*<br/>
Zeiger auf eine `LHITTESTINFO` -Struktur, enthält alle Informationen über den Link, der Benutzer geklickt hat.

### <a name="return-value"></a>Rückgabewert

Gibt "true" bei Erfolg bei "false".

### <a name="remarks"></a>Hinweise

Diese Memberfunktion implementiert das Verhalten der Win32-Nachricht [LM_HITTEST](/windows/desktop/Controls/lm-hittest), wie im Windows SDK beschrieben.

##  <a name="setitem"></a>  CLinkCtrl::SetItem

Legt fest, die Status und Attribute eines Elements der Link-Steuerelement.

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Ein Zeiger auf eine [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) Struktur mit Informationen über das festlegen.

### <a name="return-value"></a>Rückgabewert

Gibt "true" bei Erfolg bei "false".

### <a name="remarks"></a>Hinweise

Diese Memberfunktion implementiert das Verhalten der Win32-Nachricht [LM_SETITEM](/windows/desktop/Controls/lm-setitem), wie im Windows SDK beschrieben.

##  <a name="setitemid"></a>  CLinkCtrl::SetItemID

Ruft die ID des Elements eine Link-Steuerelement ab.

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>Parameter

*iLink*<br/>
Der Index eines Elements der Link-Steuerelement.

*szID*<br/>
Eine mit Null endende Zeichenfolge, die die ID des angegebenen Elements enthält.

### <a name="return-value"></a>Rückgabewert

Gibt "true" bei Erfolg bei "false".

### <a name="remarks"></a>Hinweise

Legt die ID des Elements einen bestimmten Link-Steuerelement fest. Weitere Informationen finden Sie auf die Win32-Meldung [LM_SETITEM](/windows/desktop/Controls/lm-setitem) im Windows SDK.

##  <a name="setitemstate"></a>  CLinkCtrl::SetItemState

Ruft den Zustand des Elements die Link-Steuerelement ab.

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>Parameter

*iLink*<br/>
Der Index eines Elements der Link-Steuerelement.

*pnState*<br/>
Der Wert des Elements angegebenen Status festgelegt wird.

*stateMask*<br/>
Kombination von Flags, die beschreiben die Status-Element, das festgelegt wird. Eine Liste von Werten, finden Sie unter der Beschreibung des der `state` Element in der [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) Struktur. Zulässigen Elemente sind identisch mit denen innerhalb von `state`.

### <a name="return-value"></a>Rückgabewert

Gibt "true" bei Erfolg bei "false".

### <a name="remarks"></a>Hinweise

Legt den Wert des Elements angegebenen Status einen bestimmten Link-Steuerelement ein Element. Weitere Informationen finden Sie auf die Win32-Meldung [LM_SETITEM](/windows/desktop/Controls/lm-setitem) im Windows SDK.

##  <a name="setitemurl"></a>  CLinkCtrl::SetItemUrl

Legt fest, die URL, die durch die Link-Steuerelement ein Element dargestellt wird.

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>Parameter

*iLink*<br/>
Der Index eines Elements der Link-Steuerelement.

*szUrl*<br/>
Eine Null-terminierte Zeichenfolge, die mit der URL, die durch das angegebene Element dargestellt wird

### <a name="return-value"></a>Rückgabewert

Gibt "true" bei Erfolg bei "false".

### <a name="remarks"></a>Hinweise

Legt fest, die URL, die durch den angegebenen Link-Steuerelement ein Element dargestellt wird. Weitere Informationen finden Sie auf die Win32-Meldung [LM_SETITEM](/windows/desktop/Controls/lm-setitem) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)
