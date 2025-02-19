---
title: Globale Sicherheitsfunktionen
ms.date: 11/04/2016
f1_keywords:
- atlsecurity/ATL::AtlGetDacl
- atlsecurity/ATL::AtlSetDacl
- atlsecurity/ATL::AtlGetGroupSid
- atlsecurity/ATL::AtlSetGroupSid
- atlsecurity/ATL::AtlGetOwnerSid
- atlsecurity/ATL::AtlSetOwnerSid
- atlsecurity/ATL::AtlGetSacl
- atlsecurity/ATL::AtlSetSacl
- atlsecurity/ATL::AtlGetSecurityDescriptor
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
ms.openlocfilehash: 2c9a6fd31850ed137167b6987ddf2f83f34c64a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197241"
---
# <a name="security-global-functions"></a>Globale Sicherheitsfunktionen

Diese Funktionen bieten Unterstützung für die SID und ACL-Objekte ändern.

> [!IMPORTANT]
>  In der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|||
|-|-|
|[AtlGetDacl](#atlgetdacl)|Mit dieser Funktion werden die Informationen zur freigegebenen Zugriffssteuerungsliste (DACL, Discretionary Access Control List) eines bestimmten Objekts abgerufen.|
|[AtlSetDacl](#atlsetdacl)|Mit dieser Funktion werden die Informationen zur freigegebenen Zugriffssteuerungsliste (DACL, Discretionary Access Control List) eines bestimmten Objekts festgelegt.|
|[AtlGetGroupSid](#atlgetgroupsid)|Mit dieser Funktion wird die Gruppensicherheits-ID (SID) eines Objekts abgerufen.|
|[AtlSetGroupSid](#atlsetgroupsid)|Mit dieser Funktion wird die Gruppensicherheits-ID (SID) eines Objekts festgelegt.|
|[AtlGetOwnerSid](#atlgetownersid)|Mit dieser Funktion wird die Sicherheits-ID (SID) des Besitzers eines Objekts abgerufen.|
|[AtlSetOwnerSid](#atlsetownersid)|Mit dieser Funktion wird die Sicherheits-ID (SID) des Besitzers eines Objekts festgelegt.|
|[AtlGetSacl](#atlgetsacl)|Mit dieser Funktion werden die Informationen zur Systemzugriffssteuerungsliste (SACL, System Access Control List) eines bestimmten Objekts abgerufen.|
|[AtlSetSacl](#atlsetsacl)|Mit dieser Funktion werden die Informationen zur Systemzugriffssteuerungsliste (SACL, System Access Control List) eines bestimmten Objekts festgelegt.|
|[AtlGetSecurityDescriptor](#atlgetsecuritydescriptor)|Mit dieser Funktion wird die Sicherheitsbeschreibung eines angegebenen Objekts abgerufen.|

## <a name="requirements"></a>Anforderungen

**Header:** atlsecurity.h

##  <a name="atlgetdacl"></a>  AtlGetDacl

Mit dieser Funktion werden die Informationen zur freigegebenen Zugriffssteuerungsliste (DACL, Discretionary Access Control List) eines bestimmten Objekts abgerufen.

> [!IMPORTANT]
>  Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Handle für das Objekt für die die Informationen abzurufen.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) -Enumeration, der den Typ des Objekts identifizierte gibt an die *hObject* Parameter.

*pDacl*<br/>
Zeiger auf eine DACL-Objekt, das die abgerufenen Informationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Hinweise

In Debugbuilds Assertion wird eine Fehlermeldung wenn *hObject* oder *pDacl* ist ungültig.

##  <a name="atlsetdacl"></a>  AtlSetDacl

Mit dieser Funktion werden die Informationen zur freigegebenen Zugriffssteuerungsliste (DACL, Discretionary Access Control List) eines bestimmten Objekts festgelegt.

> [!IMPORTANT]
>  Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Handle für das Objekt für das Festlegen der Sicherheitsinformationen.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) -Enumeration, der den Typ des Objekts identifizierte gibt an die *hObject* Parameter.

*rDacl*<br/>
Die DACL, die die neue Sicherheitsinformationen enthält.

*dwInheritanceFlowControl*<br/>
Die flusssteuerung für die Vererbung. Dieser Wert kann 0 (Standard), PROTECTED_DACL_SECURITY_INFORMATION oder UNPROTECTED_DACL_SECURITY_INFORMATION sein.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Hinweise

In Debugbuilds wird ein Assertionsfehler auftreten, wenn *hObject* ist ungültig, oder wenn *DwInheritanceFlowControl* ist keiner der drei zulässigen Werte.
### <a name="requirements"></a>Anforderungen

**Header:** atlsecurity.h

##  <a name="atlgetgroupsid"></a>  AtlGetGroupSid

Mit dieser Funktion wird die Gruppensicherheits-ID (SID) eines Objekts abgerufen.

> [!IMPORTANT]
>  Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Handle für das Objekt aus der Sicherheitsinformationen abgerufen werden soll.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) -Enumeration, der den Typ des Objekts identifizierte gibt an die *hObject* Parameter.

*pSid*<br/>
Zeiger auf eine `CSid` Objekt, das die neue Sicherheitsinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="requirements"></a>Anforderungen

**Header:** atlsecurity.h

##  <a name="atlsetgroupsid"></a>  AtlSetGroupSid

Mit dieser Funktion wird die Gruppensicherheits-ID (SID) eines Objekts festgelegt.

> [!IMPORTANT]
>  Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Handle für das Objekt für das Festlegen der Sicherheitsinformationen.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) -Enumeration, der den Typ des Objekts identifizierte gibt an die *hObject* Parameter.

*rSid*<br/>
Die `CSid` -Objekt, das die neue Sicherheitsinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="requirements"></a>Anforderungen

**Header:** atlsecurity.h

##  <a name="atlgetownersid"></a>  AtlGetOwnerSid

Mit dieser Funktion wird die Sicherheits-ID (SID) des Besitzers eines Objekts abgerufen.

> [!IMPORTANT]
>  Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Handle für das Objekt aus der Sicherheitsinformationen abgerufen werden soll.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) -Enumeration, der den Typ des Objekts identifizierte gibt an die *hObject* Parameter.

*pSid*<br/>
Zeiger auf eine `CSid` Objekt, das die neue Sicherheitsinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="requirements"></a>Anforderungen

**Header:** atlsecurity.h

##  <a name="atlsetownersid"></a>  AtlSetOwnerSid

Mit dieser Funktion wird die Sicherheits-ID (SID) des Besitzers eines Objekts festgelegt.

> [!IMPORTANT]
>  Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Handle für das Objekt für das Festlegen der Sicherheitsinformationen.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) -Enumeration, der den Typ des Objekts identifizierte gibt an die *hObject* Parameter.

*rSid*<br/>
Die `CSid` -Objekt, das die neue Sicherheitsinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="requirements"></a>Anforderungen

**Header:** atlsecurity.h

##  <a name="atlgetsacl"></a>  AtlGetSacl

Mit dieser Funktion werden die Informationen zur Systemzugriffssteuerungsliste (SACL, System Access Control List) eines bestimmten Objekts abgerufen.

> [!IMPORTANT]
>  Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Handle für das Objekt aus der die Informationen abgerufen werden soll.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) -Enumeration, der den Typ des Objekts identifizierte gibt an die *hObject* Parameter.

*pSacl*<br/>
Zeiger auf eine SACL-Objekt, das die abgerufenen Informationen enthält.

*bRequestNeededPrivileges*<br/>
Bei "true", versucht die Funktion die SE_SECURITY_NAME-Berechtigung aktivieren und auf den Abschluss wiederherstellen.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Hinweise

Wenn `AtlGetSacl` oft aufgerufen werden soll, auf viele verschiedene Objekte, sie werden sehr viel effizienter, die SE_SECURITY_NAME-Berechtigung zu aktivieren, einmal vor dem Aufrufen der Funktion, wobei *bRequestNeededPrivileges* auf "false" festgelegt.

### <a name="requirements"></a>Anforderungen

**Header:** atlsecurity.h

##  <a name="atlsetsacl"></a>  AtlSetSacl

Mit dieser Funktion werden die Informationen zur Systemzugriffssteuerungsliste (SACL, System Access Control List) eines bestimmten Objekts festgelegt.

> [!IMPORTANT]
>  Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Handle für das Objekt für das Festlegen der Sicherheitsinformationen.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) -Enumeration, der den Typ des Objekts identifizierte gibt an die *hObject* Parameter.

*rSacl*<br/>
Der SACL, die die neue Sicherheitsinformationen enthält.

*dwInheritanceFlowControl*<br/>
Die flusssteuerung für die Vererbung. Dieser Wert kann 0 (Standard), PROTECTED_SACL_SECURITY_INFORMATION oder UNPROTECTED_SACL_SECURITY_INFORMATION sein.

*bRequestNeededPrivileges*<br/>
Bei "true", versucht die Funktion die SE_SECURITY_NAME-Berechtigung aktivieren und auf den Abschluss wiederherstellen.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Hinweise

In Debugbuilds wird ein Assertionsfehler auftreten, wenn *hObject* ist ungültig, oder wenn *DwInheritanceFlowControl* ist keiner der drei zulässigen Werte.

Wenn `AtlSetSacl` oft aufgerufen werden soll, auf viele verschiedene Objekte, sie werden sehr viel effizienter, die SE_SECURITY_NAME-Berechtigung zu aktivieren, einmal vor dem Aufrufen der Funktion, wobei *bRequestNeededPrivileges* auf "false" festgelegt.

### <a name="requirements"></a>Anforderungen

**Header:** atlsecurity.h

##  <a name="atlgetsecuritydescriptor"></a>  AtlGetSecurityDescriptor

Mit dieser Funktion wird die Sicherheitsbeschreibung eines angegebenen Objekts abgerufen.

> [!IMPORTANT]
>  Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlGetSecurityDescriptor(
    LPCTSTR pszObjectName,
    SE_OBJECT_TYPE ObjectType,
    CSecurityDesc* pSecurityDescriptor,
    SECURITY_INFORMATION requestedInfo = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION,
bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parameter

*pszObjectName*<br/>
Zeiger auf eine auf Null endende Zeichenfolge, die den Namen des Objekts aus der abzurufenden Sicherheitsinformationen angibt.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) -Enumeration, der den Typ des Objekts identifizierte gibt an die *PszObjectName* Parameter.

*pSecurityDescriptor*<br/>
Das Objekt, das die Sicherheitsbeschreibung für die angeforderte empfängt.

*requestedInfo*<br/>
Eine Reihe von [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) Bitflags, die den Typ der abzurufenden Sicherheitsinformationen, angeben. Dieser Parameter kann eine Kombination der folgenden Werte sein.

*bRequestNeededPrivileges*<br/>
Bei "true", versucht die Funktion die SE_SECURITY_NAME-Berechtigung aktivieren und auf den Abschluss wiederherstellen.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Hinweise

Wenn `AtlGetSecurityDescriptor` oft aufgerufen werden soll, auf viele verschiedene Objekte, sie werden sehr viel effizienter, die SE_SECURITY_NAME-Berechtigung zu aktivieren, einmal vor dem Aufrufen der Funktion, wobei *bRequestNeededPrivileges* auf "false" festgelegt.

### <a name="requirements"></a>Anforderungen

**Header:** atlsecurity.h

## <a name="see-also"></a>Siehe auch

[Funktionen](../../atl/reference/atl-functions.md)
