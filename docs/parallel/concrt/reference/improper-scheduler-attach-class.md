---
title: improper_scheduler_attach-Klasse
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_attach
- CONCRT/concurrency::improper_scheduler_attach
- CONCRT/concurrency::improper_scheduler_attach::improper_scheduler_attach
helpviewer_keywords:
- improper_scheduler_attach class
ms.assetid: 5a76da0a-091b-4748-8f62-b3a28f674f9e
ms.openlocfilehash: 2d6a7b53269d305c976bcc596fe85dc018442332
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262475"
---
# <a name="improperschedulerattach-class"></a>improper_scheduler_attach-Klasse

Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn die `Attach`-Methode für ein `Scheduler`-Objekt aufgerufen wird, das bereits an den aktuellen Kontext angefügt wurde.

## <a name="syntax"></a>Syntax

```
class improper_scheduler_attach : public std::exception;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[improper_scheduler_attach](#ctor)|Überladen. Erstellt ein `improper_scheduler_attach`-Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`exception`

`improper_scheduler_attach`

## <a name="requirements"></a>Anforderungen

**Header:** concrt.h

**Namespace:** Parallelität

##  <a name="ctor"></a> improper_scheduler_attach

Erstellt ein `improper_scheduler_attach`-Objekt.

```
explicit _CRTIMP improper_scheduler_attach(_In_z_ const char* _Message) throw();

improper_scheduler_attach() throw();
```

### <a name="parameters"></a>Parameter

*_Message*<br/>
Eine beschreibende Fehlermeldung.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[Scheduler-Klasse](scheduler-class.md)
