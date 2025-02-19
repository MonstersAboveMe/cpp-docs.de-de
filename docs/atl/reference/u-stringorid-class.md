---
title: _U_STRINGorID-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
ms.openlocfilehash: 4e6c086f9d2ff4061c6404444a3b4c61dd91fe1c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197114"
---
# <a name="ustringorid-class"></a>_U_STRINGorID-Klasse

Dieses Argument-Adapterklasse ermöglicht entweder Ressourcennamen (LPCTSTRs) oder Ressourcen-IDs (jenem) an eine Funktion übergeben werden, ohne dass des Aufrufers die ID in eine Zeichenfolge, die mit dem Makro MAKEINTRESOURCE zu konvertieren.

> [!IMPORTANT]
>  Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class _U_STRINGorID
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|Der Konstruktor.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|Der Ressourcenbezeichner.|

## <a name="remarks"></a>Hinweise

Diese Klasse dient zum Implementieren von der Windows-Ressourcenverwaltungs-API-Wrapper wie z. B. die [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea), [LoadIcon](/windows/desktop/api/winuser/nf-winuser-loadicona), und [LoadMenu](/windows/desktop/api/winuser/nf-winuser-loadmenua) -Funktionen, die akzeptieren ein LPCTSTR-Argument, das möglicherweise entweder den Namen einer Ressource oder der-ID.

Die Klasse definiert zwei Konstruktorüberladungen: eine akzeptiert ein Argument LPCTSTR und die andere ein UINT-Argument akzeptiert. Konvertiert das Argument "uint" für einen Ressourcentyp, die kompatibel mit Windows Resource-Manager-Funktionen, die mithilfe der MAKEINTRESOURCE-Makro und das Ergebnis gespeichert werden, in der Klasse der einzelnen Datenmember, [M_lpstr](#_u_stringorid__m_lpstr). Das Argument an den Konstruktor LPCTSTR wird direkt ohne Konvertierung gespeichert.

## <a name="requirements"></a>Anforderungen

**Header:** atlwin.h vorhanden

##  <a name="_u_stringorid__m_lpstr"></a>  _U_STRINGorID::m_lpstr

Die Klasse enthält den Wert als einen öffentlichen Datenmember von LPCTSTR an eines ihrer Konstruktoren übergeben.

```
LPCTSTR m_lpstr;
```

##  <a name="_u_stringorid___u_stringorid"></a>  _U_STRINGorID::_U_STRINGorID

Der Konstruktor "uint" konvertiert das Argument für einen Ressourcentyp, die kompatibel mit Windows-Resource-Manager-Funktionen mit dem Makro MAKEINTRESOURCE und das Ergebnis wird gespeichert, in der Klasse der einzelnen Datenmember, [M_lpstr](#_u_stringorid__m_lpstr).

```
_U_STRINGorID(UINT nID);
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Eine Ressourcen-ID

*lpString*<br/>
Ein Ressourcenname.

### <a name="remarks"></a>Hinweise

Das Argument an den Konstruktor LPCTSTR wird direkt ohne Konvertierung gespeichert.

## <a name="see-also"></a>Siehe auch

[Übersicht über die Klasse](../../atl/atl-class-overview.md)
