---
title: IOleControlImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
ms.openlocfilehash: 50119d21b041f37f03ca416a9a56ca9e29ae3344
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276795"
---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl-Klasse

Diese Klasse stellt eine Standardimplementierung von der `IOleControl` -Schnittstelle und implementiert `IUnknown`.

> [!IMPORTANT]
>  Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Abgeleitet von die Klasse `IOleControlImpl`.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|Gibt an, ob der Container ignoriert oder Ereignisse vom Steuerelement akzeptiert.|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Fügt Informationen über die Tastaturverhalten des Steuerelements. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informiert ein Steuerelement, dass eine oder mehrere der ambient-Eigenschaften des Containers geändert hat. Es gibt S_OK zurück, die ATL-Implementierung.|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informiert dem Steuerelement, dass ein Benutzer eine angegebene Tastenkombination gedrückt hat. Die ATL-Implementierung gibt E_NOTIMPL zurück.|

## <a name="remarks"></a>Hinweise

Klasse `IOleControlImpl` stellt eine Standardimplementierung von der [IOleControl](/windows/desktop/api/ocidl/nn-ocidl-iolecontrol) -Schnittstelle und implementiert `IUnknown` durch Senden von Informationen an das Speicherabbild Gerät im Debugmodus wird erstellt.

**Verwandte Artikel** [ATL-Lernprogramm](../../atl/active-template-library-atl-tutorial.md), [Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Anforderungen

**Header:** atlctl.h

##  <a name="freezeevents"></a>  IOleControlImpl::FreezeEvents

In ATLs-Implementierung `FreezeEvents` erhöht der Control-Klasse `m_nFreezeEvents` Datenmember Wenn `bFreeze` ist "true", und dekrementiert `m_nFreezeEvents` Wenn `bFreeze` ist "false".

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Hinweise

`FreezeEvents` dann gibt S_OK zurück.

Finden Sie unter [IOleControl:: FreezeEvents](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-freezeevents) in das Windows SDK.

##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo

Fügt Informationen über die Tastaturverhalten des Steuerelements.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Hinweise

Finden Sie unter [IOleControl:GetControlInfo](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) in das Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange

Informiert ein Steuerelement, dass eine oder mehrere der ambient-Eigenschaften des Containers geändert hat.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Hinweise

Finden Sie unter [IOleControl::OnAmbientPropertyChange](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) in das Windows SDK.

##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic

Informiert dem Steuerelement, dass ein Benutzer eine angegebene Tastenkombination gedrückt hat.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Hinweise

Finden Sie unter [IOleControl::OnMnemonic](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) in das Windows SDK.

## <a name="see-also"></a>Siehe auch

[IOleObjectImpl-Klasse](../../atl/reference/ioleobjectimpl-class.md)<br/>
[ActiveX-Steuerelemente Schnittstellen](/windows/desktop/com/activex-controls-interfaces)<br/>
[Übersicht über die Klasse](../../atl/atl-class-overview.md)
