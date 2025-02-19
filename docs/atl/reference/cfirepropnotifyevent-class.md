---
title: CFirePropNotifyEvent-Klasse
ms.date: 11/04/2016
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
ms.openlocfilehash: 493bc00708d031f1bf7a4eb74d56e927a9c3f1dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245490"
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent-Klasse

Diese Klasse stellt Methoden für die Benachrichtigung des Containers-Senke in Bezug auf Änderungen von Steuerelement-Eigenschaften.

> [!IMPORTANT]
>  Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CFirePropNotifyEvent
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|(Statisch) Benachrichtigt den Container-Senke, die eine Steuerelementeigenschaft geändert wurde.|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|(Statisch) Benachrichtigt den Container-Senke, die eine Steuerelementeigenschaft geändert wird.|

## <a name="remarks"></a>Hinweise

`CFirePropNotifyEvent` verfügt über zwei Methoden, mit die des Containers Senke benachrichtigt werden, die eine Steuerelementeigenschaft geändert hat oder zu ändern.

Wenn die Klasse implementiert das Steuerelement abgeleitet wird `IPropertyNotifySink`, `CFirePropNotifyEvent` Methoden werden aufgerufen, wenn Sie aufrufen `FireOnRequestEdit` oder `FireOnChanged`. Wenn eine Klasse nicht abgeleitet ist `IPropertyNotifySink`, Aufrufe dieser Funktionen gibt S_OK zurück.

Weitere Informationen zum Erstellen von Steuerelementen finden Sie unter den [ATL-Lernprogramm](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Anforderungen

**Header:** atlctl.h

##  <a name="fireonchanged"></a>  CFirePropNotifyEvent::FireOnChanged

Benachrichtigt alle verbundenen [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) Schnittstellen (auf jeder Verbindungspunkt des Objekts), die die Eigenschaft des angegebenen Objekts geändert wurde.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parameter

*pUnk*<br/>
[in] Zeiger auf die `IUnknown` des Objekts, das die Benachrichtigung gesendet.

*dispID*<br/>
[in] Der Bezeichner der Eigenschaft, die geändert wurde.

### <a name="return-value"></a>Rückgabewert

Einer der standardmäßigen HRESULT-Werte.

### <a name="remarks"></a>Hinweise

Diese Funktion ist sicher aufgerufen werden, auch wenn das Steuerelement Verbindungspunkte nicht unterstützt.

##  <a name="fireonrequestedit"></a>  CFirePropNotifyEvent::FireOnRequestEdit

Benachrichtigt alle verbundenen [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) Schnittstellen (auf jeder Verbindungspunkt des Objekts), die die angegebene geändert wird.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parameter

*pUnk*<br/>
[in] Zeiger auf die `IUnknown` des Objekts, das die Benachrichtigung gesendet.

*dispID*<br/>
[in] Der Bezeichner der Eigenschaft zu ändern.

### <a name="return-value"></a>Rückgabewert

Einer der standardmäßigen HRESULT-Werte.

### <a name="remarks"></a>Hinweise

Diese Funktion ist sicher aufgerufen werden, auch wenn das Steuerelement Verbindungspunkte nicht unterstützt.

## <a name="see-also"></a>Siehe auch

[Übersicht über die Klasse](../../atl/atl-class-overview.md)
