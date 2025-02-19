---
title: tlbid
ms.date: 10/18/2018
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: ae79ce9245bb1c0425c3e9b92dd27b52fa443dba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179606"
---
# <a name="tlbid"></a>tlbid

**C++-spezifisch**

Ermöglicht das Laden anderer Bibliotheken als der primären Typbibliothek.

## <a name="syntax"></a>Syntax

```
tlbid(number)
```

### <a name="parameters"></a>Parameter

*Anzahl*<br/>
Die Nummer der Typbibliothek in `filename`.

## <a name="remarks"></a>Hinweise

Wenn mehrere Typbibliotheken in einer DLL, es ist möglich, beim Laden von Bibliotheken als die primäre Typbibliothek mit basieren **Tlbid**.

Zum Beispiel:

```cpp
#import <MyResource.dll> tlbid(2)
```

identisch mit folgendem Ausdruck:

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**Ende C++-spezifisch**

## <a name="see-also"></a>Siehe auch

[#import-Attribute](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import-Anweisung](../preprocessor/hash-import-directive-cpp.md)