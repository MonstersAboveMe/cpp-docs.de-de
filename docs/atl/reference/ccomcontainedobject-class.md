---
title: CComContainedObject-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
ms.openlocfilehash: 15ea9be2a3576081901c9e744d89d33688fe838a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259507"
---
# <a name="ccomcontainedobject-class"></a>CComContainedObject-Klasse

Diese Klasse implementiert [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) delegiert Vorgänge an den des Besitzerobjekts `IUnknown`.

> [!IMPORTANT]
>  Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>Parameter

*Basis*<br/>
Abgeleitet von die Klasse [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) oder [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|Der Konstruktor. Initialisiert den Zeiger Member auf, um den des Besitzerobjekts `IUnknown`.|
|[CComContainedObject::~CComContainedObject](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CComContainedObject::AddRef](#addref)|Inkrementiert den Verweiszähler für das Besitzerobjekt.|
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|Ruft ab, der des Besitzerobjekts `IUnknown`.|
|[CComContainedObject::QueryInterface](#queryinterface)|Ruft einen Zeiger auf die Schnittstelle angefordert wird, in dem Objekt ab.|
|[CComContainedObject::Release](#release)|Dekrementiert den Verweiszähler für das Besitzerobjekt.|

## <a name="remarks"></a>Hinweise

ATL verwendet `CComContainedObject` in Klassen [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md), und [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject` implementiert [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) delegiert Vorgänge an den des Besitzerobjekts `IUnknown`. (Der Besitzer ist das äußere Objekt einer Aggregation oder das Objekt, das für das eine Tearoff Schnittstelle erstellt wird.) `CComContainedObject` Aufrufe `CComObjectRootEx`des `OuterQueryInterface`, `OuterAddRef`, und `OuterRelease`, über alle geerbten `Base`.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Base`

`CComContainedObject`

## <a name="requirements"></a>Anforderungen

**Header:** atlcom.h

##  <a name="addref"></a>  CComContainedObject::AddRef

Inkrementiert den Verweiszähler für das Besitzerobjekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der möglicherweise bei der Diagnose hilfreich oder testen.

##  <a name="ccomcontainedobject"></a>  CComContainedObject::CComContainedObject

Der Konstruktor.

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>Parameter

*pv*<br/>
[in] Der des Besitzerobjekts `IUnknown`.

### <a name="remarks"></a>Hinweise

Legt die `m_pOuterUnknown` Member Zeiger (geerbt, die über die `Base` Klasse) zu *pv*.

##  <a name="dtor"></a>  CComContainedObject:: ~ CComContainedObject

Der Destruktor.

```
~CComContainedObject();
```

### <a name="remarks"></a>Hinweise

Gibt alle zugeordnete Ressourcen frei.

##  <a name="getcontrollingunknown"></a>  CComContainedObject::GetControllingUnknown

Gibt die `m_pOuterUnknown` Member Zeiger (geerbt, die über die *Base* Klasse), die der des Besitzerobjekts enthält `IUnknown`.

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>Rückgabewert

Der des Besitzerobjekts `IUnknown`.

### <a name="remarks"></a>Hinweise

Diese Methode möglicherweise virtuelle Wenn `Base` wurde deklariert die [DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) Makro.

##  <a name="queryinterface"></a>  CComContainedObject::QueryInterface

Ruft einen Zeiger auf die Schnittstelle angefordert wird, in dem Objekt ab.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parameter

*iid*<br/>
[in] Der Bezeichner der angeforderten Schnittstelle.

*ppvObject*<br/>
[out] Ein Zeiger auf den Schnittstellenzeiger vom *Iid*. Wenn das Objekt nicht über diese Schnittstelle unterstützt *PpvObject* auf NULL festgelegt ist.

*pp*<br/>
[out] Ein Zeiger auf den Schnittstellenzeiger vom Typ `Q`. Wenn das Objekt nicht über diese Schnittstelle unterstützt *pp* auf NULL festgelegt ist.

### <a name="return-value"></a>Rückgabewert

Ein standard HRESULT-Wert.

##  <a name="release"></a>  CComContainedObject::Release

Dekrementiert den Verweiszähler für das Besitzerobjekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Rückgabewert

In Debugbuilds `Release` gibt einen Wert an, die möglicherweise bei der Diagnose hilfreich oder Tests zurück. In nicht-Debugbuilds `Release` gibt immer 0 zurück.

## <a name="see-also"></a>Siehe auch

[Übersicht über die Klasse](../../atl/atl-class-overview.md)
