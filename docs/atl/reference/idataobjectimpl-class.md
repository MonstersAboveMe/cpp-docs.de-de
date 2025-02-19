---
title: IDataObjectImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl::DAdvise
- ATLCTL/ATL::IDataObjectImpl::DUnadvise
- ATLCTL/ATL::IDataObjectImpl::EnumDAdvise
- ATLCTL/ATL::IDataObjectImpl::EnumFormatEtc
- ATLCTL/ATL::IDataObjectImpl::FireDataChange
- ATLCTL/ATL::IDataObjectImpl::GetCanonicalFormatEtc
- ATLCTL/ATL::IDataObjectImpl::GetData
- ATLCTL/ATL::IDataObjectImpl::GetDataHere
- ATLCTL/ATL::IDataObjectImpl::QueryGetData
- ATLCTL/ATL::IDataObjectImpl::SetData
helpviewer_keywords:
- data transfer [C++]
- data transfer [C++], Uniform Data Transfer
- IDataObjectImpl class
- IDataObject, ATL implementation
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
ms.openlocfilehash: b73cfe83075b9595bc98ca05ab2ec2e1771a038d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275463"
---
# <a name="idataobjectimpl-class"></a>IDataObjectImpl-Klasse

Diese Klasse stellt Methoden für die Unterstützung, Uniform Data Transfer und Verwalten von Verbindungen.

> [!IMPORTANT]
>  Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Abgeleitet von die Klasse `IDataObjectImpl`.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[IDataObjectImpl::DAdvise](#dadvise)|Herstellen einer Verbindung zwischen dem Datenobjekt und einer Advise-Senke. Dies ermöglicht die Advise-Senke zum Empfangen von Benachrichtigungen über Änderungen im-Objekt.|
|[IDataObjectImpl::DUnadvise](#dunadvise)|Beendet eine Verbindung zuvor mit `DAdvise`.|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Erstellt einen Enumerator zum Durchlaufen der aktuellen Advise-Verbindungen.|
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Erstellt einen Enumerator zum Durchlaufen der `FORMATETC` Strukturen, die vom Datenobjekt unterstützt. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IDataObjectImpl::FireDataChange](#firedatachange)|Sendet eine Benachrichtigung an jede Advise-Senke.|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Ruft eine logisch äquivalente `FORMATETC` Struktur, die komplexer ist. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IDataObjectImpl::GetData](#getdata)|Überträgt Daten aus dem Datenobjekt an den Client an. Die Daten werden beschrieben eine `FORMATETC` strukturieren und übertragen wird, über eine `STGMEDIUM` Struktur.|
|[IDataObjectImpl::GetDataHere](#getdatahere)|Ähnlich wie `GetData`, außer dass der Client zuweisen, muss die `STGMEDIUM` Struktur. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IDataObjectImpl::QueryGetData](#querygetdata)|Bestimmt, ob das Datenobjekt, das eine bestimmte unterstützt `FORMATETC` Struktur zum Übertragen von Daten. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IDataObjectImpl::SetData](#setdata)|Überträgt Daten vom Client, auf das Datenobjekt. Die ATL-Implementierung gibt E_NOTIMPL zurück.|

## <a name="remarks"></a>Hinweise

Die [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) Schnittstelle stellt Methoden zur Unterstützung von Uniform Data Transfer. `IDataObject` verwendet die Strukturen Standardformat [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) und [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) zum Abrufen und Speichern von Daten.

`IDataObject` Außerdem verwaltet Verbindungen herstellen, um das empfehlen von senken, änderungsbenachrichtigungen für Daten zu behandeln. Implementieren des Clients muss in der Reihenfolge für den Client zum Empfangen von änderungsbenachrichtigungen für Daten aus dem Datenobjekt, das [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) Schnittstelle für ein Objekt, das eine Advisesenke aufgerufen haben. Wenn der Client ruft dann `IDataObject::DAdvise`, eine Verbindung zwischen dem Datenobjekt und der Advise-Senke hergestellt wird.

Klasse `IDataObjectImpl` stellt eine Standardimplementierung von `IDataObject` und implementiert `IUnknown` durch Senden von Informationen an das Speicherabbild Gerät im Debugmodus wird erstellt.

**Verwandte Artikel** [ATL-Lernprogramm](../../atl/active-template-library-atl-tutorial.md), [Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>Anforderungen

**Header:** atlctl.h

##  <a name="dadvise"></a>  IDataObjectImpl::DAdvise

Herstellen einer Verbindung zwischen dem Datenobjekt und einer Advise-Senke.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Hinweise

Dies ermöglicht die Advise-Senke zum Empfangen von Benachrichtigungen über Änderungen im-Objekt.

Um die Verbindung zu beenden, rufen Sie [DUnadvise](#dunadvise).

Finden Sie unter [IDataObject::DAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dadvise) in das Windows SDK.

##  <a name="dunadvise"></a>  IDataObjectImpl::DUnadvise

Beendet eine Verbindung zuvor mit [DAdvise](#dadvise).

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>Hinweise

Finden Sie unter [IDataObject::DUnadvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dunadvise) in das Windows SDK.

##  <a name="enumdadvise"></a>  IDataObjectImpl::EnumDAdvise

Erstellt einen Enumerator zum Durchlaufen der aktuellen Advise-Verbindungen.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Hinweise

Finden Sie unter [IDataObject::EnumDAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-enumdadvise) in das Windows SDK.

##  <a name="enumformatetc"></a>  IDataObjectImpl::EnumFormatEtc

Erstellt einen Enumerator zum Durchlaufen der `FORMATETC` Strukturen, die vom Datenobjekt unterstützt.

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>Hinweise

Finden Sie unter [IDataObject::EnumFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-enumformatetc) in das Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

##  <a name="firedatachange"></a>  IDataObjectImpl::FireDataChange

Sendet eine Benachrichtigung an jede Advise-Senke, die gerade verwaltet wird.

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>Rückgabewert

Ein standard HRESULT-Wert.

##  <a name="getcanonicalformatetc"></a>  IDataObjectImpl::GetCanonicalFormatEtc

Ruft eine logisch äquivalente `FORMATETC` Struktur, die komplexer ist.

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Hinweise

Finden Sie unter [IDataObject::GetCanonicalFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) in das Windows SDK.

##  <a name="getdata"></a>  IDataObjectImpl::GetData

Überträgt Daten aus dem Datenobjekt an den Client an.

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>Hinweise

Die *PformatetcIn* Parameter muss einen Speichermedientyp TYMED_MFPICT angeben.

Finden Sie unter [IDataObject:: GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) in das Windows SDK.

##  <a name="getdatahere"></a>  IDataObjectImpl::GetDataHere

Ähnlich wie `GetData`, außer dass der Client zuweisen, muss die `STGMEDIUM` Struktur.

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Hinweise

Finden Sie unter [IDataObject::GetDataHere](/windows/desktop/api/objidl/nf-objidl-idataobject-getdatahere) in das Windows SDK.

##  <a name="querygetdata"></a>  IDataObjectImpl::QueryGetData

Bestimmt, ob das Datenobjekt, das eine bestimmte unterstützt `FORMATETC` Struktur zum Übertragen von Daten.

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Hinweise

Finden Sie unter [IDataObject::QueryGetData](/windows/desktop/api/objidl/nf-objidl-idataobject-querygetdata) in das Windows SDK.

##  <a name="setdata"></a>  IDataObjectImpl::SetData

Überträgt Daten vom Client, auf das Datenobjekt.

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Hinweise

Finden Sie unter [IDataObject::SetData](/windows/desktop/api/objidl/nf-objidl-idataobject-setdata) in das Windows SDK.

## <a name="see-also"></a>Siehe auch

[Übersicht über die Klasse](../../atl/atl-class-overview.md)
